---

## ✅ Valid Feedback Results for 4-Color Guesses (No Repeats)

The following feedback outcomes are valid when:
- The secret contains **4 distinct colors**
- The guess also contains **4 distinct colors**
- The total number of available colors is 6

### ✅ Valid Feedbacks (12 total):

```
(0,1), (0,2), (0,3), (0,4),
(1,0), (1,1), (1,2),
(2,0), (2,1), (2,2),
(3,0),
(4,0)
```

### ❌ Invalid Feedbacks (examples):

| Feedback | Reason |
|----------|--------|
| (0, 0)   | Impossible: with 4 guessed colors and only 6 total colors, there must be overlap |
| (3, 1)   | Impossible: would imply all 4 guess colors match with only 3 in correct position — but no 4th match is possible |
