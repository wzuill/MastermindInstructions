# Plan: Next Steps in Static Mastermind Deduction Logic

This plan outlines the immediate next stage in developing the deduction system for a static Mastermind solver based on Greenwell’s fixed guesses. It builds on the completed logic for 2-color (2×2) guesses and continues the development of a reasoning framework for progressively more complex guess types.

---

## ✅ Completed

- Structured deduction logic for 2-color, 2×2 guesses.
- Symbolic system: `✓`, `?`, `X`, `—`.
- Feedback table for all six valid feedback outcomes in 2-color guesses.
- Guidelines.md fully updated and verified.
- Clarified distinction between **guess order** and **analysis order**.

---

## 🔭 Primary Focus: 3-Color Guess Deduction Logic

We will now develop deduction rules and constraints for guesses involving **three distinct colors**, such as `(A, B, C, B)` or `(A, A, B, C)`.

This will include:

### Step 1 — Define Feedback Possibilities
- List all valid feedback combinations for 3-color guesses under the no-duplicate-colors rule.
- Validate impossibilities like `(3, 1)` or `(2, 2)` based on reasoning constraints.

### Step 2 — Construct Feedback Deduction Table
For each valid feedback outcome:
- Indicate whether each color is possibly in the code.
- Use a deduction matrix to show:
  - `✓` — confirmed color and position.
  - `?` — possible color in position.
  - `X` — color cannot be in position.
  - `—` — color was not guessed in that position.
- Write a clear **structural interpretation** of what the feedback implies.

### Step 3 — Work Through Example Guesses
- Select 1–2 representative 3-color guesses from Greenwell’s fixed set.
- Simulate various feedbacks.
- Walk through constraint updates using the deduction matrix.
- Identify ambiguity patterns that require cross-guess reasoning.

---

## Optional (Later)
- Repeat similar work for 4-color guesses once 3-color patterns are understood.
- Begin exploring deduction strategy (how to order feedbacks for maximum early clarity).

---

## Outcome
This work will extend the symbolic deduction system and build the logic foundation for solving all Greenwell static guess combinations by deduction — without brute force.