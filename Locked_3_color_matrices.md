
# 🔒 Locked Feedback Deduction Matrix for 3-Color Guess (A, B, C, B)

For each feedback result, the table below shows:
- `✓` — This color is confirmed to be in the secret code
- `?` — This color or position might be valid, but cannot be confirmed
- `X` — This color or position is eliminated as invalid

### Feedback (0, 1)
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | X      | ?      | ?      | ?      |
| B     | ?        | ?      | X      | ?      | X      |
| C     | ?        | ?      | ?      | X      | ?      |

### Feedback (0, 2)
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | X      | ?      | ?      | ?      |
| B     | ?        | ?      | X      | ?      | X      |
| C     | ?        | ?      | ?      | X      | ?      |

### Feedback (0, 3)
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ✓        | X      | ?      | ?      | ?      |
| B     | ✓        | ?      | X      | ?      | X      |
| C     | ✓        | ?      | ?      | X      | ?      |

### Feedback (1, 0)
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | X      | X      | X      |
| B     | ?        | X      | ?      | X      | ?      |
| C     | ?        | X      | X      | ?      | X      |

### Feedback (1, 1)
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | ?      | ?      | ?      |
| B     | ?        | ?      | ?      | ?      | ?      |
| C     | ?        | ?      | ?      | ?      | ?      |

### Feedback (1, 2)
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ✓        | ?      | ?      | ?      | ?      |
| B     | ✓        | ?      | ?      | ?      | ?      |
| C     | ✓        | ?      | ?      | ?      | ?      |

### Feedback (2, 0)
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ?        | ?      | X      | X      | X      |
| B     | ?        | X      | ?      | X      | ?      |
| C     | ?        | ?      | X      | ?      | X      |

### Feedback (3, 0)
| Color | In Code? | Pos 0 | Pos 1 | Pos 2 | Pos 3 |
|-------|----------|--------|--------|--------|--------|
| A     | ✓        | ✓      | X      | X      | X      |
| B     | ✓        | X      | ?      | X      | ?      |
| C     | ✓        | X      | X      | ✓      | X      |
