# Reasoning for Deduction Matrix – Feedback (2, 1)

**Guess:** (A, B, C, D)  
**Feedback:** 2 black, 1 white

---

## Interpretation of Feedback

- **2 black pegs**: Two guessed colors are in the secret code and in the correct positions.
- **1 white peg**: One guessed color is in the secret code but in the wrong position.
- **Remaining color**: Not in the secret at all.

This means:
- Exactly **three** of the guessed colors are in the secret.
- One color is completely excluded from the secret.
- Of the included ones:
  - Two must be at their guessed positions.
  - One must be at a different position.

---

## Deduction Principles Applied

1. **Cannot Identify Which Are Which**:
   - We do not know which specific color is excluded.
   - We do not know which are black pegs (correct position).
   - We do not know which is the white peg (wrong position).

2. **Ambiguity Prevents Position Elimination**:
   - Each color could be:
     - One of the black pegs → in correct position (✓ in guessed position, X elsewhere)
     - The white peg → in wrong position (X in guessed position, ? elsewhere)
     - Or the excluded one → X in all positions
   - Since we cannot tell which role each color plays, no deductions are possible yet.

3. **Conservative Deduction**:
   - The only safe move is to mark all positions for all colors as `?`
   - We must defer deeper deductions until a second guess narrows the roles.

---

## Final Deduction Matrix (2, 1)

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | ?      | ?      | ?      |
| B     | ?        | ?      | ?      | ?      | ?      |
| C     | ?        | ?      | ?      | ?      | ?      |
| D     | ?        | ?      | ?      | ?      | ?      |

This matrix captures the maximum uncertainty — three colors are in, but we don’t know their roles.
