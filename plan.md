# Plan for Deduction Logic Development

## ✅ Completed Focus: 2-Color Guess Deduction Logic

We have defined deduction rules and constraints for guesses involving **two distinct colors**, such as (A, A, B, B).

This included:

### Step 1 — Define Feedback Possibilities
- Feedback combinations: (0,0), (0,1), (0,2), (1,0), (1,1), (2,0)
- All others are invalid given the no-duplicate constraint.

### Step 2 — Construct Feedback Deduction Table
- For each feedback result, we used a 4-symbol system:
  - `✓` — confirmed position
  - `?` — possible but not confirmed
  - `X` — eliminated
  - `—` — unguessed
- Inclusion column also tracks:
  - `✓` — in secret
  - `?` — unknown
  - `X` — not in secret
- These are embedded in `guidelines.md`.

### Step 3 — Lock Down Logic
- All valid feedback patterns locked into `guidelines.md`.
- Confirmed table for (A, A, B, B) type guess.

---

## ✅ Completed Focus: 3-Color Guess Deduction Logic

We have developed deduction rules and constraints for guesses involving **three distinct colors**, such as (A, B, C, B).

### Step 1 — Define Feedback Possibilities
- Valid combinations:
  - (0,1), (0,2), (0,3), (1,0), (1,1), (1,2), (2,0), (3,0)
- Invalid:
  - (0,0) — cannot happen with 3 distinct and all 4 positions filled

### Step 2 — Construct Feedback Deduction Table
- For each valid feedback result, a full deduction table was created:
  - Color
  - In Code?
  - Pos 0–3
- Marked with `✓`, `?`, `X`, `—` where appropriate.
- Logic aligned with locked principles.
- Final verified matrix embedded in `guidelines.md`.

### Step 3 — Work Through Example Guesses
- We reviewed example feedbacks for each type.
- Carefully validated positional and inclusion logic.
- Locked each case once confirmed.

---

## 🔭 Next Focus: 4-Color Guess Deduction Logic

We will now develop deduction rules and constraints for guesses involving **four distinct colors**, such as `(A, B, C, D)`.

This phase will include:

### Step 1 — Define Feedback Possibilities
- Enumerate all valid feedback combinations for 4-color guesses.
- Feedback may range from `(0, 0)` to `(4, 0)` and all in between.
- Include all (black, white) pairs where black + white ≤ 4.

### Step 2 — Construct Feedback Deduction Table
For each valid feedback outcome:
- Use a deduction matrix to show:
  - `✓` — confirmed color and position.
  - `?` — possible color in position.
  - `X` — color cannot be in position.
  - `—` — color was not guessed in that position.
- Indicate if each color is:
  - Confirmed in the secret code (`✓`)
  - Not in the code (`X`)
  - Still uncertain (`?`)
- Add to `guidelines.md` once confirmed.

### Step 3 — Confirm Impossibility of Duplicate Colors
- Validate that all deductions and feedbacks honor the no-duplicate rule.
- Explicitly disallow feedback results that would require color repetition in the secret.

### Step 4 — Analyze Key Patterns
- Identify feedbacks that yield strong immediate constraints.
- Study patterns where two positions can be confirmed or eliminated.
- Prepare for solver code to handle this feedback type.
