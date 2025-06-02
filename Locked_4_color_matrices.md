# 🔒 Locked Feedback Deduction Matrices for 4-Color Distinct Guesses

Each matrix below applies to a guess with four distinct colors, e.g., (A, B, C, D), and the specified feedback result.

## 🎯 Valid Feedback for 4-Color Distinct Guesses

Only the following 11 feedback combinations are valid under the "no-duplicate colors" rule. These are based on the constraint that the secret code uses 4 **distinct** colors, drawn from 6 available colors:

| Black Pegs | White Pegs                                                       | Meaning |
| ---------- | ---------------------------------------------------------------- | ------- |
| (4, 0)     | All four guessed colors are correct and in the correct positions |         |
| (3, 0)     | Three correct in position, one not in secret                     |         |
| (2, 2)     | Two correct in position, two correct in wrong positions          |         |
| (2, 1)     | Two correct in position, one correct in wrong position           |         |
| (2, 0)     | Two correct in position, two not in secret                       |         |
| (1, 3)     | One correct in position, three correct in wrong positions        |         |
| (1, 2)     | One correct in position, two correct in wrong positions          |         |
| (1, 1)     | One correct in position, one correct in wrong position           |         |
| (0, 4)     | All four guessed colors are correct but in the wrong positions   |         |
| (0, 3)     | Three guessed colors are correct but in the wrong positions      |         |
| (0, 2)     | Two guessed colors are correct but in the wrong positions        |         |

Any feedback not in this list (such as (3,1), (0,1), or (0,0)) is logically inconsistent with the four-color no-duplicate constraint and must be treated as invalid.

### Feedback (4, 0)

All four guessed colors are in the secret and in the correct positions. This is the only case where the code is completely known after a single guess.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ✓        | ✓     | X     | X     | X     |
| B     | ✓        | X     | ✓     | X     | X     |
| C     | ✓        | X     | X     | ✓     | X     |
| D     | ✓        | X     | X     | X     | ✓     |

---

### Feedback (3, 0)

Three of the guessed colors are in the secret and in the correct positions. One color is not in the secret. We cannot determine which color is excluded or which positions are correct yet, so no positions can be confirmed or eliminated.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ?        | ?     | ?     | ?     | ?     |
| B     | ?        | ?     | ?     | ?     | ?     |
| C     | ?        | ?     | ?     | ?     | ?     |
| D     | ?        | ?     | ?     | ?     | ?     |

---

### Feedback (0, 2)

Exactly two of the guessed colors are in the secret, but in the wrong positions. The other two colors are not in the secret.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ?        | X     | ?     | ?     | ?     |
| B     | ?        | ?     | X     | ?     | ?     |
| C     | ?        | ?     | ?     | X     | ?     |
| D     | ?        | ?     | ?     | ?     | X     |

### Feedback (0, 3)

Three of the guessed colors are in the secret, but all in the wrong positions. One color is not in the secret at all.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ?        | X     | ?     | ?     | ?     |
| B     | ?        | ?     | X     | ?     | ?     |
| C     | ?        | ?     | ?     | X     | ?     |
| D     | ?        | ?     | ?     | ?     | X     |

### Feedback (0, 4)

All four guessed colors are in the secret but in the wrong positions.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ✓        | X     | ?     | ?     | ?     |
| B     | ✓        | ?     | X     | ?     | ?     |
| C     | ✓        | ?     | ?     | X     | ?     |
| D     | ✓        | ?     | ?     | ?     | X     |

### Feedback (1, 1)

One guessed color is in the correct position (black), one is in the secret but in the wrong position (white), and two are not in the secret. We do not yet know which is which.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ?        | ?     | ?     | ?     | ?     |
| B     | ?        | ?     | ?     | ?     | ?     |
| C     | ?        | ?     | ?     | ?     | ?     |
| D     | ?        | ?     | ?     | ?     | ?     |

### Feedback (1, 2)

Three guessed colors are in the secret — one in the correct position (black), two in the wrong positions (white). One color is not in the secret. We cannot identify which is which yet.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ?        | ?     | ?     | ?     | ?     |
| B     | ?        | ?     | ?     | ?     | ?     |
| C     | ?        | ?     | ?     | ?     | ?     |
| D     | ?        | ?     | ?     | ?     | ?     |

### Feedback (1, 3)

All four guessed colors are in the secret. One is in the correct position (black), and the other three are in the wrong positions (white). We do not yet know which is which.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ✓        | ?     | ?     | ?     | ?     |
| B     | ✓        | ?     | ?     | ?     | ?     |
| C     | ✓        | ?     | ?     | ?     | ?     |
| D     | ✓        | ?     | ?     | ?     | ?     |

### Feedback (2, 1)

Two of the guessed colors are in the secret and in the correct positions. One other color is in the secret but in the wrong position. One color is not in the secret at all. We do not yet know which is which.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ?        | ?     | ?     | ?     | ?     |
| B     | ?        | ?     | ?     | ?     | ?     |
| C     | ?        | ?     | ?     | ?     | ?     |
| D     | ?        | ?     | ?     | ?     | ?     |

### Feedback (2, 0)

Two of the guessed colors are in the secret and are in the correct positions. The other two guessed colors are not in the secret at all. However, we do not yet know which colors these are, so we cannot eliminate or confirm any positions.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ?        | ?     | ?     | ?     | ?     |
| B     | ?        | ?     | ?     | ?     | ?     |
| C     | ?        | ?     | ?     | ?     | ?     |
| D     | ?        | ?     | ?     | ?     | ?     |

### Feedback (2, 2)

Two of the guessed colors are in the secret and in the correct positions. Two others are in the secret but in the wrong positions. All four guessed colors are part of the secret code. We do not know which are black or white, so no positions can be confirmed or eliminated yet.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
| ----- | -------- | ----- | ----- | ----- | ----- |
| A     | ✓        | ?     | ?     | ?     | ?     |
| B     | ✓        | ?     | ?     | ?     | ?     |
| C     | ✓        | ?     | ?     | ?     | ?     |
| D     | ✓        | ?     | ?     | ?     | ?     |
