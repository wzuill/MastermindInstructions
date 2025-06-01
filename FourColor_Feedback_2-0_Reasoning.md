# Reasoning for Deduction Matrix – Feedback (2, 0)

**Guess:** (A, B, C, D)  
**Feedback:** 2 black, 0 white

---

## Interpretation of Feedback

- **2 black pegs**: Two guessed colors are in the secret code and are in the correct positions.
- **0 white pegs**: No other guessed colors are present in the secret code at all.

---

## Deduction Principles Applied

1. **Two Colors Are in the Secret**:
   - But we do not know which two.
   - Therefore, we cannot mark any color as definitely included (✓) or excluded (X) from the "In Code?" column.
   - All guessed colors are marked as `?` for "In Code?"

2. **Correct Positions Only**:
   - The two correct colors are in their exact guessed positions.
   - Therefore, if a color is in the code, it must be in the position it was guessed.
   - For each color, we retain `?` in the guessed position column and eliminate (`X`) all other positions.

3. **Two Colors Are NOT in the Secret**:
   - These colors are entirely absent from the secret code.
   - Since we do not know which ones, we cannot remove any row.
   - But: for each color, if it is not in the code, then all its positions are `X`.

4. **Implication of No Whites**:
   - No color can be in a different position from where it was guessed.
   - So even for the colors that *are* in the code, they must be in the same position.
   - Therefore: we eliminate all positions **except** the guessed one for each color.

---

## Final Deduction Matrix (2, 0)

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | X      | X      | X      |
| B     | ?        | X      | ?      | X      | X      |
| C     | ?        | X      | X      | ?      | X      |
| D     | ?        | X      | X      | X      | ?      |

This matrix expresses all valid information derivable from feedback (2,0) with a 4-color distinct guess.
