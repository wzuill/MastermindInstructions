# 🧩 RuleLoader Design and Deduction Rule Interpretation

## 🎯 Purpose

The `RuleLoader` is a key infrastructure component in the Mastermind Static Solver. It interprets and applies canonical deduction rules — defined in locked matrix files — to actual guesses and feedbacks during code deduction.

These matrices are **not exhaustive mappings** of every guess and feedback. Instead, they are **examples of patterns** (e.g., (A, A, B, B)) from which rule logic can be generalized.

## 🔄 Core Role

`RuleLoader` does not return a static matrix. Instead, it:

1. Identifies the **structural pattern** of a guess.
2. Matches that pattern and feedback pair to a **canonical deduction rule**.
3. Translates the canonical symbols (A, B, C, D) to actual colors in the guess.
4. Applies deduction implications (✓, ?, X) to the evolving `DeductionState`.

## 🧠 Guess Pattern Categories

| Type    | Structure Example | Notes                              |
| ------- | ----------------- | ---------------------------------- |
| 2-color | (A, A, B, B)      | Only 6 valid feedbacks             |
| 3-color | (A, B, C, B)      | 8 valid feedbacks; includes repeat |
| 4-color | (A, B, C, D)      | 11 valid feedbacks; all distinct   |

## 📦 `RuleLoader` Responsibilities

### 1. Pattern Classification

```java
GuessPatternType fromGuess(Guess g);
```

* Determines whether guess is 2-color, 3-color, or 4-color type
* Captures repetition structure (e.g., A, A, B, B)

### 2. Rule Selection

```java
DeductionRule getRule(GuessPatternType type, Feedback feedback);
```

* Returns a generalized rule (e.g., for (A, A, B, B) + (1, 0))
* Rules are loaded from locked matrix markdown files

### 3. Rule Application

```java
interface DeductionRule {
    void apply(Guess guess, Feedback feedback, DeductionState state);
}
```

* Translates canonical positions and colors to actual guess values
* Applies deductions to the shared state (inclusion, exclusion, position info)

## 📘 Example: Translating a Canonical Rule

### Actual Input

```text
Guess: (4, 5, 4, 5)
Feedback: (1, 1)
```

### RuleLoader:

* Detects pattern: (A, A, B, B) → 2-color
* Retrieves rule for: 2-color + (1,1)
* Applies rule with A=4, B=5
* Updates `DeductionState`:

    * 4 and 5 are both in code (✓)
    * No positions can be confirmed yet (all ?)

## 📊 Output Interface

Rule application affects a shared state object:

```java
class DeductionState {
    Map<Integer, Boolean> colorInCode;
    Map<Integer, Set<Integer>> eliminatedPositions;
    Map<Integer, Integer> confirmedPositions;
    // ... other constraints
}
```

## ✅ Benefits

* Avoids brute force by applying structured deduction
* Canonical rules remain simple and reusable
* Decouples pattern recognition from deduction logic
* Enables static correctness guarantees and microtesting

## 🚧 Next Step

Implement a library of `DeductionRule` classes for each:

* (2-color) × 6 feedbacks
* (3-color) × 8 feedbacks
* (4-color) × 11 feedbacks

These rule handlers can be small classes or lambdas injected via the loader.

---

This component is the engine that turns pattern-based deduction into working code logic, consistent with the static solver's no-brute-force constraint.
