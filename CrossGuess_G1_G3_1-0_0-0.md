# Cross-Guess Deduction: G1 = (0,1,1,0) → (1,0) and G3 = (2,2,0,0) → (0,0)

## Summary of Deductions

We analyze the combined feedback of two static guesses:

- **G1 = (0, 1, 1, 0)** → Feedback: (1, 0)
- **G3 = (2, 2, 0, 0)** → Feedback: (0, 0)

---

## Step 1: Deduction from G3

- Feedback (0, 0) means none of the guessed colors are in the secret.
- G3 guesses: 2, 2, 0, 0
- Therefore:
  - Color 2 is **not in the code**
  - Color 0 is **not in the code**

These colors can be marked as excluded from **all** positions.

---

## Step 2: Deduction from G1 (informed by G3)

- G1 guesses: 0, 1, 1, 0
- Feedback: (1, 0)
- Since we now know color 0 is not in the code, it contributes **nothing** to feedback.
- Therefore, feedback (1, 0) is entirely due to the two 1s in positions 1 and 2.
- (1, 0) means:
  - One color is in the correct position
  - No color is in the wrong position

Thus:
- Color 1 is in the secret exactly **once**, and it is in the correct position.
- One of the two positions (1 or 2) is correct for color 1.
- The other is incorrect, and the extra `1` must be excluded.
- Since color 1 was not guessed in positions 0 or 3, and didn’t contribute feedback from there, it **cannot** be in those positions either.

---

## ✅ Final Deduction Matrix

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | X        | X      | X      | X      | X      |
| 1     | ✓        | X      | ?      | ?      | X      |
| 2     | X        | X      | X      | X      | X      |

---

## Interpretation

- Color 0 and color 2 are fully eliminated.
- Color 1 is known to be in the code at exactly one position, either 1 or 2 — we cannot yet determine which.
- Positions 0 and 3 for color 1 are ruled out due to their absence in G1 and lack of contribution to feedback.
