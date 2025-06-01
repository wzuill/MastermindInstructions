# Reasoning for Deduction Matrix – Feedback (2, 2)

**Guess:** (A, B, C, D)  
**Feedback:** 2 black, 2 white

---

## Interpretation of Feedback

- **2 black pegs**: Two colors are in the secret and in the correct position.
- **2 white pegs**: Two other colors are in the secret but in the wrong position.
- Therefore, all four guessed colors are in the secret.

---

## Deduction Principles Applied

1. **All Colors Are Included**:
   - All four guessed colors are confirmed to be in the secret code.
   - Mark “In Code?” as `✓` for each.

2. **Position Ambiguity**:
   - Each guessed color could either be a black peg (correct position) or a white peg (wrong position).
   - Therefore, we cannot confirm or eliminate any position for any color.

3. **Conservative Deduction**:
   - All positions for all four colors are marked `?`.

---

## Final Deduction Matrix (2, 2)

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ✓        | ?      | ?      | ?      | ?      |
| B     | ✓        | ?      | ?      | ?      | ?      |
| C     | ✓        | ?      | ?      | ?      | ?      |
| D     | ✓        | ?      | ?      | ?      | ?      |

This matrix reflects the maximum allowable certainty from feedback (2,2): all colors are present, but positional roles remain unknown.
