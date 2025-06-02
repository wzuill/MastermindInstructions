# Scenario_02: Alternate Feedback Path for Static Guesses

This scenario analyzes a different set of feedback responses for the standard six fixed static guesses in Mastermind, based on Greenwell’s sequence. The goal is to apply the locked deduction rules to determine the secret code using only logical inference.

---

## 📋 Scenario Overview: Guesses and Feedback

| Guess # | Guess         | Feedback        |
|---------|---------------|-----------------|
| G1      | (0, 1, 1, 0)  | (0 black, 2 white) |
| G2      | TBD           | TBD             |
| G3      | (2, 2, 0, 0)  | (2 black, 0 white) |
| G4      | TBD           | TBD             |
| G5      | (4, 5, 4, 5)  | (0 black, 0 white) |
| G6      | TBD           | TBD             |
---

## ✅ Deductions from G1 = (0, 1, 1, 0) → (0, 2)

### Feedback Interpretation
- **0 black**: None of the guessed colors are in the correct position.
- **2 white**: Two of the guessed colors are in the secret code, but in wrong positions.

### Guess Details
- Colors guessed: 0 and 1
- Distribution: Color 0 at pos 0 and 3; Color 1 at pos 1 and 2

### Deduction Logic
- One instance of color 0 and one of color 1 are in the secret.
- Their positions in the guess are not correct.

### Deduction Matrix
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | ?      | ?      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |

---

## ✅ Deductions from G3 = (2, 2, 0, 0) → (2, 0)

### Feedback Interpretation
- **2 black**: Two guessed colors are in the secret and in the correct position.
- **0 white**: No other guessed colors are in the secret.
- Colors guessed: 2 and 0, each repeated twice.

### Deduction Logic
- Colors 2 and 0 are both in the secret once each.
- One instance of each is in the correct position (black); the duplicate is not.
- Therefore:
  - For color 0: one of pos 2 or 3 is correct, the other is not.
  - For color 2: one of pos 0 or 1 is correct, the other is not.

### Cross-Guess Resolution for Color 0
- From G1, we already eliminated pos 0 and 3 for color 0.
- That leaves only pos 2 for color 0 → must be correct.

### Updated Deduction Matrices

#### Color 0 — Now fully resolved:
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | X      | ✓      | X      |

#### Color 1 — from G1 (in code, wrong at 1 and 2):
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 1     | ✓        | ?      | X      | X      | ?      |

#### Color 2 — from G3 (in code, one ✓ at pos 0 or 1):
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 2     | ✓        | ?      | ?      | X      | X      |

---

## 🔁 Summary of Known Constraints (after G1 and G3)

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | X      | ✓      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |
| 2     | ✓        | ?      | ?      | X      | X      |

We have confirmed three of the secret code's colors and significantly narrowed their possible positions.
---

## ✅ Deductions from G5 = (4, 5, 4, 5) → (0, 0)

### Feedback Interpretation
- **0 black** and **0 white** means **none** of the guessed colors are in the secret.
- Colors guessed: 4 and 5
- Therefore, both are completely excluded from the secret.

### Confirmed Eliminations
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 4     | ❌        | X      | X      | X      | X      |
| 5     | ❌        | X      | X      | X      | X      |

---

## 🔐 Cross-Guess Deduction: All Four Colors in the Secret

From combined reasoning across G1, G3, and G5:

- ✅ **Color 0** is in the secret (confirmed at pos 2)
- ✅ **Color 1** is in the secret (not at pos 1 or 2)
- ✅ **Color 2** is in the secret (not at pos 2 or 3)
- ✅ **Color 3** is the only unguessed and uneliminated color → must be the fourth color

This locks in the complete set of secret code colors: **0, 1, 2, 3**

---

## 🧾 Updated Deduction Matrix (after G5)

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | X      | ✓      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |
| 2     | ✓        | ?      | ?      | X      | X      |
| 3     | ✓        | ?      | ?      | ?      | ?      |
| 4     | ❌        | X      | X      | X      | X      |
| 5     | ❌        | X      | X      | X      | X      |