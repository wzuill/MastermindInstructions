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

### 🔄 Guess Order vs. Analysis Order
In the static version of Mastermind using Greenwell’s six fixed guesses, **all guesses are made before any feedback is analyzed**. The **order in which the guesses are made does not matter** to the correctness of the final solution.

However, the **order in which feedback is analyzed** can influence the **clarity, speed, and simplicity** of deduction.

- Some feedback results (e.g., `(0, 0)` or `(2, 0)`) may yield strong immediate constraints and are often easiest to analyze first.
- Deductions may be more effective when **processed in an order that eliminates ambiguity early** or isolates specific colors or positions.
- This mirrors how a human might work: mentally prioritizing the most definitive clues, even though all guesses are already fixed.

> Therefore, while the **guess set is fixed and unordered**, the **analysis order is strategic** and may be chosen dynamically based on the feedbacks received.

---

## 🔢 Valid Feedback by Guess Type

### One Distinct Color (e.g. `(0, 0, 0, 0)`)
Possible feedback outcomes:
- `(1, 0)`
- `(0, 0)`

### Two Distinct Colors (e.g. `(0, 1, 1, 0)` or `(2, 3, 3, 2)`)
Possible feedback outcomes:
- `(2, 0)`
- `(1, 1)`
- `(1, 0)`
- `(0, 2)`
- `(0, 1)`
- `(0, 0)`

### Three Distinct Colors (e.g. `(0, 1, 2, 1)` or `(2, 3, 4, 2)`)
Possible feedback outcomes:
- `(3, 0)`
- `(2, 1)`
- `(2, 0)`
- `(1, 2)`
- `(1, 1)`
- `(1, 0)`
- `(0, 2)`
- `(0, 1)`
- `(0, 0)` ❌ Invalid (cannot occur with 3 distinct colors and no duplicates)

### Four Distinct Colors (e.g. `(0, 1, 2, 3)` or `(3, 4, 5, 0)`)

Only the following 11 feedback results are possible and should be supported for deduction logic:

(4,0) — All four colors correct and in correct positions  
(3,0) — Three correct in position, one color not in secret  
(2,2) — Two correct in position, two correct in wrong position  
(2,1) — Two correct in position, one correct in wrong position  
(2,0) — Two correct in position, two not in secret  
(1,3) — One correct in position, three correct in wrong positions  
(1,2) — One correct in position, two correct in wrong positions  
(1,1) — One correct in position, one correct in wrong position  
(0,4) — All four guessed colors are correct but in wrong positions  
(0,3) — Three guessed colors are correct but in wrong positions  
(0,2) — Two guessed colors are correct but in wrong positions

The following feedbacks **cannot** occur under the 4-distinct-color constraint and must be treated as invalid:

(3,1) — Impossible due to color reuse conflict (would require 5 distinct colors in secret)  
(1,0) — Requires 3 secret colors not in guess (not enough available colors)  
(0,1) — Requires 3 secret colors not in guess (not enough available colors)  
(0,0) — Requires 4 secret colors not in guess (impossible with only 6 total colors)

Any feedback outside the valid set above should be treated as logically inconsistent under the no-duplicates rule and must not be allowed during deduction processing.

---

## ❗ Constraint: Feedback Limitations for 2-Color Guesses

When a guess contains only **two distinct colors**, and the secret code contains **no duplicate colors**, then the **maximum number of total pegs (black + white)** in feedback is **2**.

Therefore, the only valid feedback combinations for 2-color guesses are:
- `(0, 0)`
- `(0, 1)`
- `(0, 2)`
- `(1, 0)`
- `(1, 1)`
- `(2, 0)`

All other feedback values — such as `(1, 2)`, `(2, 1)`, or `(2, 2)` — are **impossible** under this constraint and should be treated as invalid.

This rule helps detect feedback errors and reduces the deduction search space.

---
