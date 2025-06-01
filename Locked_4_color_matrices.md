# 🔒 Locked Feedback Deduction Matrices for 4-Color Distinct Guesses

Each matrix below applies to a guess with four distinct colors, e.g., (A, B, C, D), and the specified feedback result.

### Feedback (0, 2)
Exactly two of the guessed colors are in the secret, but in the wrong positions. The other two colors are not in the secret.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | X      | ?      | ?      | ?      |
| B     | ?        | ?      | X      | ?      | ?      |
| C     | ?        | ?      | ?      | X      | ?      |
| D     | ?        | ?      | ?      | ?      | X      |

### Feedback (0, 3)
Three of the guessed colors are in the secret, but all in the wrong positions. One color is not in the secret at all.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | X      | ?      | ?      | ?      |
| B     | ?        | ?      | X      | ?      | ?      |
| C     | ?        | ?      | ?      | X      | ?      |
| D     | ?        | ?      | ?      | ?      | X      |

### Feedback (0, 4)
All four guessed colors are in the secret but in the wrong positions.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ✓        | X      | ?      | ?      | ?      |
| B     | ✓        | ?      | X      | ?      | ?      |
| C     | ✓        | ?      | ?      | X      | ?      |
| D     | ✓        | ?      | ?      | ?      | X      |

### Feedback (1, 1)
One guessed color is in the correct position (black), one is in the secret but in the wrong position (white), and two are not in the secret. We do not yet know which is which.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | ?      | ?      | ?      |
| B     | ?        | ?      | ?      | ?      | ?      |
| C     | ?        | ?      | ?      | ?      | ?      |
| D     | ?        | ?      | ?      | ?      | ?      |

### Feedback (1, 2)
Three guessed colors are in the secret — one in the correct position (black), two in the wrong positions (white). One color is not in the secret. We cannot identify which is which yet.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | ?      | ?      | ?      |
| B     | ?        | ?      | ?      | ?      | ?      |
| C     | ?        | ?      | ?      | ?      | ?      |
| D     | ?        | ?      | ?      | ?      | ?      |

### Feedback (1, 3)
All four guessed colors are in the secret. One is in the correct position (black), and the other three are in the wrong positions (white). We do not yet know which is which.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ✓        | ?      | ?      | ?      | ?      |
| B     | ✓        | ?      | ?      | ?      | ?      |
| C     | ✓        | ?      | ?      | ?      | ?      |
| D     | ✓        | ?      | ?      | ?      | ?      |

### Feedback (2, 1)
Two of the guessed colors are in the secret and in the correct positions. One other color is in the secret but in the wrong position. One color is not in the secret at all. We do not yet know which is which.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | ?      | ?      | ?      |
| B     | ?        | ?      | ?      | ?      | ?      |
| C     | ?        | ?      | ?      | ?      | ?      |
| D     | ?        | ?      | ?      | ?      | ?      |

### Feedback (2, 0)
Two of the guessed colors are in the secret and are in the correct positions. The other two guessed colors are not in the secret at all. However, we do not yet know which colors these are, so we cannot eliminate or confirm any positions.

| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | ?      | ?      | ?      |
| B     | ?        | ?      | ?      | ?      | ?      |
| C     | ?        | ?      | ?      | ?      | ?      |
| D     | ?        | ?      | ?      | ?      | ?      |
