# Cross-Guess Deduction: G2 = (1, 2, 4, 3) → (2, 1)

## Context

This deduction builds on prior locked results from guesses G1, G3, and G5:

| Color | In Code? |
|-------|----------|
| 0     | ❌        |
| 1     | ✅        |
| 2     | ❌        |
| 3     | ✅        |
| 4     | ✅        |
| 5     | ✅        |

Secret colors: **1, 3, 4, 5**

---

## Guess G2: (1, 2, 4, 3)  
**Feedback**: (2 black, 1 white)

| Pos | Color |
|-----|--------|
|  0  |   1    |
|  1  |   2    |
|  2  |   4    |
|  3  |   3    |

From prior knowledge:
- Color 2 is not in the secret → Pos 1 is a guaranteed miss
- Colors 1, 3, 4 are all in the secret

Feedback (2 black, 1 white) means:
- Exactly one of the three in-code colors is in the wrong position → white
- The other two are in the correct position → black
- Color 2 contributes nothing to feedback

---

## Deduction

We analyze which combination of black and white pegs is possible:

- If color 1 (pos 0) were a black peg, then either 3 or 4 would have to be the white peg
- However, if 1 were correct at pos 0, this would contradict earlier feedback from G1, where 1 was at pos 1 and 2, and 0s (non-code) were at 0 and 3, and feedback was (1, 0)
- That implies 1 must be in the code but **not at pos 0 or 3**

Therefore, in G2:
- Color 1 at pos 0 must be the white peg (correct color, wrong position)
- Colors 4 at pos 2 and 3 at pos 3 must be the two black pegs (correct color, correct position)

---

## Final Positional Deductions

- **Color 4** is black at position 2
- **Color 3** is black at position 3
- **Color 1** is white at position 0 → must be placed elsewhere

---

## ✅ Updated Deduction Matrix

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ❌        | X      | X      | X      | X      |
| 1     | ✓        | X      | ?      | ?      | X      |
| 2     | ❌        | X      | X      | X      | X      |
| 3     | ✓        | ?      | ?      | ?      | ✓      |
| 4     | ✓        | ?      | ?      | ✓      | ?      |
| 5     | ✓        | ?      | ?      | ?      | ?      |

---

## Next Steps

While this deduction yields definitive placements for colors 3 and 4, and rules out color 1 from positions 0 and 3, further deductions may be possible through cross-analysis. This current state is saved as a consistent and locked milestone.
