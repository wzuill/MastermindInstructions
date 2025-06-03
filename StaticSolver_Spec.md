# 📘 Specification: Mastermind Static Solver (Greenwell Strategy)

## 1. 🎯 Purpose

This application is a static Mastermind solver built in Java. It uses Greenwell's six fixed guesses to deduce a 4-color secret code drawn from 6 distinct colors (0–5), without any brute force. All deduction is done through fixed logic and pre-validated reasoning matrices.

## 2. 🎮 Game Parameters

* **Pegs per code:** 4
* **Colors available:** 6 (values 0–5)
* **Duplicates in secret:** ❌ Not allowed
* **Duplicates in guesses:** ✅ Allowed
* **Number of guesses used:** Exactly 6 (fixed set)

## 3. 🎲 Greenwell’s Six Fixed Guesses

| Guess # | Guess        |
| ------- | ------------ |
| G1      | (0, 1, 1, 0) |
| G2      | (1, 2, 4, 3) |
| G3      | (2, 2, 0, 0) |
| G4      | (3, 4, 1, 3) |
| G5      | (4, 5, 4, 5) |
| G6      | (5, 5, 3, 2) |

## 4. 🧠 Deduction Logic Requirements

* Guesses are submitted in full without intermediate analysis.
* Feedback is collected for each guess as a pair: (black pegs, white pegs).
* Deduction proceeds by interpreting all six feedbacks in combination using:

  * Valid feedback sets for 2-, 3-, and 4-color guesses (see `guidelines.md`).
  * Locked reasoning matrices (see `Locked_3_color_matrices.md`, `Locked_4_color_matrices.md`).
  * Scenario-based deduction examples (see `Scenario_01.md`, `Scenario_02.md`, `Scenario_03.md`).
* Brute force is explicitly disallowed. No enumeration or filtering of valid secret codes (360 total, all 4-color, no duplicates) is permitted.

## 5. 🧱 Core Classes (Sketch)

* `StaticSolver`: orchestrates guessing and deduction.
* `Feedback`: represents black and white pegs result.
* `Guess`: wraps a 4-color guess.
* `DeductionEngine`: applies cross-guess reasoning to identify the one valid secret.
* `GameEmulator` (for testing): holds a known secret and returns feedback for guesses.
* `DeductionMatrix`: internal logic structures and constraints per feedback result.

## 6. 🔁 Guess Submission Model

* All six guesses are submitted immediately.
* Feedback is stored and passed as input to the deduction engine.
* No adaptive logic is used between guesses.

## 7. 🧪 Testing and Validation

* Solver must correctly deduce all **360 valid secrets** (4-color codes from {0–5}, no duplicates).
* Microtests must validate each deduction step individually.
* Deduction logic should reject impossible feedback values.

## 8. 🔒 Constraints Summary

* Feedbacks for guesses with 2 or 3 distinct colors must conform to strict peg count limits.
* 4-color guesses only allow 11 specific feedback values.
* No code candidate list may be constructed.
* All deduction must result from fixed reasoning paths defined in advance.

## 9. 🚀 Output Format

* Final output is the deduced 4-digit secret code.
* Optionally, a matrix of deductions may be printed.
* Guesses and feedbacks should be logged step-by-step.

---

This spec incorporates all guidelines, deduction logic constraints, and structure needed to implement the Java-based Mastermind Static Solver using Greenwell’s method.
