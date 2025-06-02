
# Scenario_02: Alternate Feedback Path for Static Guesses

This scenario analyzes a different set of feedback responses for the standard six fixed static guesses in Mastermind, based on Greenwell’s sequence. The goal is to apply the locked deduction rules to determine the secret code using only logical inference.

---

## 📋 Scenario Overview: Guesses and Feedback

| Guess # | Guess         | Feedback  |
|---------|---------------|-----------|
| G1      | (0, 1, 1, 0)  | (0 black, 2 white) |
| G2      | TBD           | TBD       |
| G3      | TBD           | TBD       |
| G4      | TBD           | TBD       |
| G5      | TBD           | TBD       |
| G6      | TBD           | TBD       |

We will proceed through the feedbacks one at a time, adding analysis and deductions for each.

---

## ✅ Deductions from G1 = (0, 1, 1, 0) → (0, 2)

### Feedback Interpretation
- **0 black**: None of the guessed colors are in the correct position.
- **2 white**: Two of the guessed colors are in the secret code, but in wrong positions.

### Guess Details
- Colors guessed: 0 and 1
- Distribution: Color 0 at pos 0 and 3; Color 1 at pos 1 and 2

### Deduction Logic
- Only **two pegs match**, and all are white.
- Therefore, one instance of **color 0** and one instance of **color 1** are in the secret.
- These correct instances are **not** at the guessed positions.

### Deduction Matrix
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ✓        | X      | ?      | ?      | X      |
| 1     | ✓        | ?      | X      | X      | ?      |

This deduction aligns with the locked matrix for a 2-color guess with (0,2) feedback.

---

(Additional guesses and reasoning to follow as feedback is provided.)
