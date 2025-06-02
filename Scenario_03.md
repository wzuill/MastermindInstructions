# Scenario_03: Cross-Guess Deduction Using Greenwell Static Guesses

This scenario explores a new feedback path for the six fixed static guesses devised by Greenwell. As before, we assume a secret code composed of **4 distinct colors** from the set {0, 1, 2, 3, 4, 5}, and all deductions must follow the locked reasoning matrices and constraints from previous deduction files.

---

## 📋 Scenario Overview: Guesses and Feedback

| Guess # | Guess         | Feedback            |
|---------|---------------|---------------------|
| G1      | (0, 1, 1, 0)  | (0 black, 2 white)  |
| G2      | (1, 2, 4, 3)  | TBD                 |
| G3      | (2, 2, 0, 0)  | (1 black, 1 white)  |
| G4      | (3, 4, 1, 3)  | TBD                 |
| G5      | (4, 5, 4, 5)  | (1 black, 0 white)  |
| G6      | (5, 5, 3, 2)  | TBD                 |

---

## 🔒 Project Rules (Summary)

- Secret uses **4 distinct** colors from 0–5
- Feedback pegs:
  - **Black** = correct color in correct position
  - **White** = correct color in wrong position
- Feedback constrained by guess type:
  - 2-color guesses: max of 2 pegs
  - 3-color guesses: max of 3 pegs
  - 4-color guesses: only 11 feedback types valid (see `guidelines.md`)
- All deduction must conform to locked logic and matrices

---

## ✅ Deduction Section (To Be Completed Incrementally)

### ✅ Deductions from G1 = (0, 1, 1, 0) → (0 black, 2 white)

- Guess includes only two colors: 0 and 1
- Color 0 appears at positions 0 and 3
- Color 1 appears at positions 1 and 2
- Feedback (0, 2) means:
  - Exactly one instance of 0 and one instance of 1 are in the secret, but in the wrong positions
  - The other instances of 0 and 1 are not contributing pegs

#### Deduction Matrix Update

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | ?      | ?      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |

- Color 0 is not at pos 0 or 3 → `X`
- Color 1 is not at pos 1 or 2 → `X`
- Both are in the secret somewhere else → `✓` for inclusion

### ✅ Deductions from G3 = (2, 2, 0, 0) → (1 black, 1 white)

- Guess includes only colors 2 and 0
- Feedback: 1 black, 1 white

Implications:
- Exactly one of the four pegs is correct in color and position
- One other peg is correct in color but at the wrong position
- The remaining two pegs are not in the secret

From G1, we already know:
- Color 0 is in the secret
- Positions 0 and 3 are excluded for color 0

Now:
- Feedback confirms color 0 contributes either the black or white peg
- The other peg must come from color 2

But we do not know whether color 2 is in the secret or not — it might be the black or white peg contributor, or one of the excluded ones

### Conservative Matrix Update

From this feedback and prior deductions:
- G1 confirms color 0 is in the code
- G3 gives (1 black, 1 white) for guess (2, 2, 0, 0)
- Since 0 is already known to be in the code, one of the pegs in G3 must come from color 2
- Therefore, color **2 must also be in the code** — the only way to generate the second peg

Thus, colors 0, 1, and 2 are all confirmed to be in the secret

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | ?      | ?      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |
| 2     | ✓        | ?      | ?      | ?      | ?      |

We defer a definitive position or exclusion for color 2 until further guesses.

### ✅ Deductions from G5 = (4, 5, 4, 5) → (1 black, 0 white)

- Colors guessed: 4 and 5 (each appears twice)
- Feedback: 1 black, 0 white

Implications:
- Exactly one of these colors is in the secret code and is in the correct position
- The other color is not in the secret at all
- One of the two instances of the included color is in the correct position; the other is not

We do not yet know which color is excluded and which is included, nor which position is correct

### Conservative Matrix Update

At this point, we know:
- Colors 0, 1, and 2 are in the code
- G5 tells us that exactly one of 4 or 5 is in the code
- That accounts for all 4 secret colors

➡️ Therefore, **color 3 is not in the secret** — it is excluded.

We mark:
- Color 4: one of two copies could be black, or color 4 might be the excluded one
- Color 5: same ambiguity
- We cannot rule out or confirm either inclusion or position yet

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 4     | ?        | ?      | ?      | ?      | ?      |
| 5     | ?        | ?      | ?      | ?      | ?      |

We will refine this once more feedbacks or eliminations appear.

---

## 🎯 Final Deduction Matrix (to be filled when complete)

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | ?      | ?      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |
| 2     | ✓        | ?      | ?      | ?      | ?      |
| 3     | ❌        | X      | X      | X      | X      |
| 4     | ?        | ?      | ?      | ?      | ?      |
| 5     | ?        | ?      | ?      | ?      | ?      |
