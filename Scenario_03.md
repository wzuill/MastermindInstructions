# Scenario_03: Cross-Guess Deduction Using Greenwell Static Guesses

This scenario explores a new feedback path for the six fixed static guesses devised by Greenwell. As before, we assume a secret code composed of **4 distinct colors** from the set {0, 1, 2, 3, 4, 5}, and all deductions must follow the locked reasoning matrices and constraints from previous deduction files.

---

## 📋 Scenario Overview: Guesses and Feedback

| Guess # | Guess         | Feedback            |
|---------|---------------|---------------------|
| G1      | (0, 1, 1, 0)  | (0 black, 2 white)  |
| G2      | (1, 2, 4, 3)  | (1 black, 2 white)  |
| G3      | (2, 2, 0, 0)  | (1 black, 1 white)  |
| G4      | (3, 4, 1, 3)  | (0 black, 2 white)  |
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

Thus, color **2 must also be in the code** — the only way to account for both pegs

#### Matrix Update

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 2     | ✓        | ?      | ?      | ?      | ?      |

### ✅ Deductions from G5 = (4, 5, 4, 5) → (1 black, 0 white)

- Colors guessed: 4 and 5 (each appears twice)
- Feedback: 1 black, 0 white

Implications:
- Exactly one of these colors is in the secret code and is in the correct position
- The other color is not in the secret at all

We do not yet know which color is excluded and which is included

At this point, we know:
- Colors 0, 1, and 2 are in the code
- G5 tells us that exactly one of 4 or 5 is in the code
- That accounts for all 4 secret colors

➡️ Therefore, **color 3 is not in the secret** — it is excluded

### ✅ Deductions from G2 = (1, 2, 4, 3) → (1 black, 2 white)

- All four guessed colors are already determined:
  - 1: in the code
  - 2: in the code
  - 4: in the code
  - 3: **not in the code** (already excluded)

Feedback: (1 black, 2 white) means:
- Three of the guessed colors are in the secret
- One is not — that is color 3

So:
- Colors 1, 2, and 4 contribute the pegs (1 black, 2 white)
- One of them is in the correct position
- Two are correct colors in wrong positions

We cannot yet determine which color is which peg, but this cross-confirms that:
- 4 is the color included from {4, 5}
- 5 is not in the code

#### Matrix Update

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 4     | ✓        | ?      | X      | ?      | X      |
| 5     | ❌        | X      | X      | X      | X      |

### ✅ Deductions from G4 = (3, 4, 1, 3) → (0 black, 2 white)

- Guessed colors: 3, 4, 1, 3
- Feedback: (0 black, 2 white)

Analysis:
- Color 3 is **not in the code** (already excluded), so cannot contribute
- Colors 4 and 1 are in the code and must contribute the 2 white pegs
- That means:
  - Color 4 is not in position 1 (its guess location)
  - Color 1 is not in position 2 (its guess location)

This provides new positional exclusions.

#### Matrix Update

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 4     | ✓        | ?      | X      | ?      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |

---

## 🎯 Final Deduction Matrix (to be filled when complete)

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | ?      | ?      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |
| 2     | ✓        | ?      | ?      | ?      | ?      |
| 3     | ❌        | X      | X      | X      | X      |
| 4     | ✓        | ?      | X      | ?      | X      |
| 5     | ❌        | X      | X      | X      | X      |
