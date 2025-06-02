# Cross-Guess Deduction Summary: Full Reasoning Leading to Forced Solution

This analysis uses the feedback from G1, G3, G5, and G2 to deduce the exact secret code under the constraints of static Mastermind with no duplicate colors.

---

## 🔒 Project Rules

- Secret uses **4 distinct colors** from {0, 1, 2, 3, 4, 5}
- No color repeats in the secret
- Feedback pegs:
  - **Black** = correct color and correct position
  - **White** = correct color, wrong position
- A color in the guess can generate **at most one peg** (either black or white), even if guessed multiple times

---

## ✅ Deductions from G3 = (2, 2, 0, 0) → (0, 0)

- Colors **2** and **0** are not in the secret
- Eliminated entirely

---

## ✅ Deductions from G1 = (0, 1, 1, 0) → (1, 0)

- 0 is eliminated ⇒ contributes nothing
- Only 1 contributes
- Two 1s in the guess, and feedback is (1 black, 0 white)
- → Color 1 is in the secret **exactly once**, and is in the **correct position** at **either pos 1 or pos 2**

---

## ✅ Deductions from G5 = (4, 5, 4, 5) → (1 black, 1 white)

- Colors 4 and 5 are used (each appears twice)
- Feedback implies:
  - **Both 4 and 5 are in the secret**
  - Each contributes one peg (no duplicates allowed in the secret or in feedback)
  - We cannot yet determine which position is which, but we confirm both are in the code

---

## ✅ Deductions from G2 = (1, 2, 4, 3) → (2 black, 1 white)

- Color 2 is eliminated ⇒ contributes nothing
- Colors 1, 4, and 3 are in the secret
- Three matching colors yield 3 feedback pegs → one must be white, two must be black

By position:

- Pos 0 = 1  
- Pos 1 = 2 (miss)  
- Pos 2 = 4  
- Pos 3 = 3

To satisfy (2 black, 1 white):
- Color 4 at pos 2 = black (✓)
- Color 3 at pos 3 = black (✓)
- Color 1 at pos 0 = white ⇒ correct color, wrong position

Since color 1 is **not** correct at pos 0, and can only be at pos 1 or 2 (from G1), and pos 2 is now occupied by 4, that leaves:

✅ Color 1 must be at **position 1**

---

## 🔁 Final Step: Deduce Color 5’s Position

We now have 3 of the 4 secret positions placed:

| Position | Color |
|----------|--------|
| 1        | 1      |
| 2        | 4      |
| 3        | 3      |

Only position left: **position 0**

The only unplaced color: **5**

✅ Therefore, **color 5 must be at position 0**

---

## 🎯 Final Answer

| Position | Color |
|----------|--------|
| 0        | 5      |
| 1        | 1      |
| 2        | 4      |
| 3        | 3      |

This configuration:
- Uses 4 distinct colors from {1, 3, 4, 5}
- Matches every locked deduction
- Explains all feedbacks correctly
- Is **logically forced** from static analysis alone

---

## ✅ Final Deduction Matrix

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| 0     | ❌        | X      | X      | X      | X      |
| 1     | ✓        | X      | ✓      | X      | X      |
| 2     | ❌        | X      | X      | X      | X      |
| 3     | ✓        | X      | X      | X      | ✓      |
| 4     | ✓        | X      | X      | ✓      | X      |
| 5     | ✓        | ✓      | X      | X      | X      |

All placements are logically forced from the existing locked deductions and feedbacks.
