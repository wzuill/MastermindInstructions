# Guidelines for ChatGPT

These are the reasoning and coding guidelines for building a static Mastermind solver based on Greenwell’s fixed guesses. These instructions are to be followed by ChatGPT when constructing code, tests, and deduction logic for this problem.

## General Principles
- Write code in small, verifiable steps, confirming correctness through focused microtests.
- Make no assumptions about feedback behavior — all reasoning must be explicitly justified.
- The secret code is always a 4-color code drawn from 6 available colors, with **no repeated colors**.
- Guesses may include repeated colors, but final deduction logic must respect the uniqueness constraint of the secret.

## Code Structure
- Separate logic into clear responsibilities: feedback analysis, constraint tracking, and deduction propagation.
- Use descriptive and precise class and method names.
- Keep each class focused on a single responsibility.
- Where possible, treat sets of possible values as immutable to avoid side-effects.

## Testing (Microtests)
- Each method should be verified by its own test case.
- Avoid combining multiple logical behaviors in one test.
- Assert constraint refinements explicitly (e.g., exclusion of a color from a position).
- Include tests for both presence and absence of specific deductions.

## Deduction Logic
- Compare feedback results across multiple guesses to rule out or confirm options.
- Apply each feedback rule and propagate consequences through all known constraints.
- Once a position is resolved to a single color, treat it as known and use it to further reduce other positions.
- Never hard-code solution outcomes; all solutions must emerge through reproducible deduction.

### Deduction Patterns by Guess Type

#### One Distinct Color (e.g. `(0, 0, 0, 0)`)
Possible feedback outcomes:
- `(1, 0)`
- `(0, 0)`

#### Two Distinct Colors (e.g. `(0, 1, 1, 0)` or `(2, 3, 3, 2)`)
Possible feedback outcomes:
- `(2, 0)`
- `(1, 1)`
- `(1, 0)`
- `(0, 2)`
- `(0, 1)`
- `(0, 0)`

#### Three Distinct Colors (e.g. `(0, 1, 2, 1)` or `(2, 3, 4, 2)`)
Possible feedback outcomes:
- `(3, 0)`
- `(2, 1)`
- `(2, 0)`
- `(1, 2)`
- `(1, 1)`
- `(1, 0)`
- `(0, 2)`
- `(0, 1)`
- `(0, 0)`

#### Four Distinct Colors (e.g. `(0, 1, 2, 3)` or `(3, 4, 5, 0)`)
Possible feedback outcomes:
- `(4, 0)`
- `(3, 0)`
- `(2, 2)`
- `(2, 1)`
- `(2, 0)`
- `(1, 3)`
- `(1, 2)`
- `(1, 1)`
- `(1, 0)`
- `(0, 4)`
- `(0, 3)`
- `(0, 2)`
- `(0, 1)`
- `(0, 0)`

### ❗ Constraint: Feedback Limitations for 2-Color Guesses

When a guess contains only **two distinct colors** (e.g. `(A, B, B, A)`), and the secret code contains **no duplicate colors**, then the **maximum number of total pegs (black + white)** in feedback is **2**.

Therefore, the only valid feedback combinations for 2-color guesses are:

- `(0, 0)`
- `(0, 1)`
- `(0, 2)`
- `(1, 0)`
- `(1, 1)`
- `(2, 0)`

All other feedback values — such as `(1, 2)`, `(2, 1)`, or `(2, 2)` — are **impossible** under this constraint and should be treated as invalid.

This rule helps detect feedback errors and reduces the deduction search space.

### 📘 Lookup Table for Deduction from 2-Color Guesses

This table summarizes the structural meaning of each valid feedback outcome when the guess contains exactly two distinct colors and the secret code contains no repeated colors.

| Feedback | Color A in Code? | Color B in Code? | Position Elimination              | Notes / Structural Inference                                                                 |
|----------|------------------|------------------|-----------------------------------|----------------------------------------------------------------------------------------------|
| `(0, 0)` | ❌ not present    | ❌ not present    | Eliminate A and B from all positions | Both guessed colors are absent from the secret.                                              |
| `(1, 0)` | ✅ one is correct in correct position, other is absent |                          | Only guessed positions are candidates for correct color; eliminate both from other positions | One of A or B is correct and in the correct place; the other is not present. Cannot determine which. |
| `(0, 1)` | ✅ one is correct in wrong position, other is absent |                          | Eliminate A and B from guessed positions; non-guessed positions are candidates | One color is in the code, but not where guessed. Cannot determine which color. |
| `(1, 1)` | ✅ present        | ✅ present        | All guessed positions are possible (`?`) | One color is correct and in correct position, one correct but misplaced. Cannot assign which. |
| `(0, 2)` | ✅ present        | ✅ present        | Eliminate guessed positions for both colors | Both colors are correct but in wrong positions. Only non-guessed positions are candidates. |
| `(2, 0)` | ✅ present        | ✅ present        | Guessed positions are likely correct; eliminate others | Both colors are in correct positions. May promote to resolved with other guesses.             |

> These interpretations should not be applied in isolation — constraints become most effective when combined across multiple guesses.

## Edge Rules
- A feedback of `(0, 0)` means none of the guessed colors appear in the secret.
- If a color appears multiple times in a guess but receives fewer matching pegs than its appearances, it can appear **at most once** in the code — or not at all — under the uniqueness rule.

## Game Roles and Behavior

### CodeMaster
- Randomly selects a valid secret code from all permutations of 4 colors out of 6 (no repeats).
- Evaluates guesses and returns correct feedback `(black, white)`.

### Player (Solver)
- Uses Greenwell’s 6 static guesses in this order, placing the simpler 2-color guesses first:
  1. `(0, 1, 1, 0)`
  2. `(2, 2, 0, 0)`
  3. `(4, 5, 4, 5)`
  4. `(1, 2, 4, 3)`
  5. `(3, 4, 1, 3)`
  6. `(5, 5, 3, 2)`

> This ordering is intentional to leverage early simplification through known deduction patterns for 2-color guesses before progressing to more complex structures.

- Collects feedback for each guess.
- Applies deduction rules and constraints based on feedback.
- Must always return a solution that is:
  - A valid 4-color permutation with no repeats.
  - Consistent with all six feedbacks received.

## Output
- The solver must output the same result every time for a given set of feedbacks (deterministic).
- The result must match one of the 360 valid codes and satisfy all logical constraints.

---

Follow these principles exactly to support explainable reasoning and consistent behavior.
