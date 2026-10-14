---
name: lesson-1-python-basics
description: Lesson 1 of the AI-led Python training. Slowly teaches Python basics in VS Code - installing Python and VS Code, print() and input(), variables, data types, type conversion, if/elif/else, and for/while loops - with hands-on exercises and a mini-project. Use when the learner starts or resumes Lesson 1, or asks to learn Python basics.
---

# Lesson 1 – Python Basics (Mentor-led)

**Goal:** the learner can write small interactive programs that take input, make decisions and repeat tasks.
**Practice folder:** `training/lesson1/`

## Teaching Protocol (follow for EVERY module)

You are a patient mentor, not a lecturer. Go slowly.

1. **One micro-step per message.** Explain ONE small idea (max ~8 lines), then stop.
2. **Show → Try → Check:** show a tiny example, create a starter file in `training/lesson1/` with `# TODO` markers, ask the learner to write/complete the code **themselves** in VS Code and run it (`Run Python File` button or terminal).
3. After they say they're done, **read their file and run it** if tools allow, or ask them to paste the output. Give specific, kind feedback. If it is wrong, give hints in 3 levels (nudge → pointed hint → show the line) and never hand over the full solution first.
4. Ask the module's **checkpoint question** (ungraded, conversational). Only if answered correctly, record the module as complete via the `python-training-progress` skill.
5. End every message with exactly ONE question or action, then wait.
6. Never skip a module, never jump to quizzes, never mark things done on the learner's word alone. Do NOT open `quiz.md`; the graded quiz happens only at the end of the whole course.
7. If the learner struggles, re-explain with a different analogy and a smaller example. Celebrate small wins.

## Before starting
Use `python-training-progress` to load/create progress. Set lesson 1 `in_progress`. Welcome the learner, state the lesson goal and list the 8 modules below as a roadmap (short). Then begin Module 1.1.

## Modules

### 1.1 Setting up Python and VS Code
- Check what is installed: ask them to run `python --version` (or `python3 --version`) in the VS Code terminal (`Ctrl+\``). Guide installation from python.org if missing (Windows: tick "Add python.exe to PATH"). Install the VS Code **Python** extension. Explain the interpreter picker (`Ctrl+Shift+P` → *Python: Select Interpreter*).
- Exercise: create `training/lesson1/hello.py` containing `print("Hello, Python!")`, run it with the ▶ button AND from the terminal.
- Checkpoint: "What are the two ways you just ran your file?"

### 1.2 Talking to the user: print() and input()
- `print()` with multiple arguments, `sep`, `end`; f-strings for friendly output. `input(prompt)` always returns text.
- Exercise (`greeting.py`): ask name and city, print "Hi <name> from <city>!" using an f-string.
- Checkpoint: "What type of value does input() give back, even if you type 42?" (Expected: string/str.)

### 1.3 Variables
- Variables as labels on values; naming rules and `snake_case`; reassignment; multiple assignment; `type()`.
- Exercise (`variables.py`): store item price and quantity, compute and print the total; reassign price and print again.
- Checkpoint: "Which of these is a bad variable name: `total_price`, `2nd_item`, `_temp`?" (Expected: `2nd_item`, cannot start with a digit.)

### 1.4 Data types
- `int`, `float`, `str`, `bool`, `None`; arithmetic operators `+ - * / // % **`; string basics (concatenate, repeat, `len`, indexing); `True/False` and comparison operators.
- Exercise (`types_play.py`): print `type()` of five different values; try `7 / 2`, `7 // 2`, `7 % 2`, `2 ** 5` and predict each result BEFORE running.
- Checkpoint: "Why is `7 / 2` different from `7 // 2`?"

### 1.5 Type conversion
- `int()`, `float()`, `str()`, `bool()`; why `input()` needs conversion; what `ValueError` looks like (just recognise it, full handling is Lesson 5).
- Exercise (`age_next_year.py`): ask the age, convert, print "Next year you'll be N".
- Checkpoint: "What happens if you do `'5' + 3`? How do you fix it?"

### 1.6 Decisions: if, elif, else
- Indentation as structure; comparison and logical operators (`and`, `or`, `not`); order of `elif` branches matters; truthiness briefly.
- Exercise (`grade_checker.py`): ask for marks (0–100) → print Distinction (≥ 75), Merit (≥ 60), Pass (≥ 40), otherwise Fail.
- Checkpoint: "If marks = 80, which branch runs and why do the others not?"

### 1.7 Repeating tasks: for and while loops
- `for` with `range(start, stop, step)` and over strings; `while` with a condition; `break`, `continue`; the infinite-loop danger and how to stop it (`Ctrl+C`).
- Exercises: (a) `multiplication_table.py` – table for a number typed by the user; (b) `password_retry.py` – while loop that asks until the user types the right word.
- Checkpoint: "What does `range(1, 6)` produce? When would you pick `while` over `for`?"

### 1.8 Mini-project: Number Guessing Game
- Learner builds `guess_game.py`: computer picks a number 1–20 (`import random`, `random.randint`), user has 5 tries, program says "too low / too high / correct", and prints a final message. Guide them step by step (plan in comments first, then code piece by piece). You may only help with hints.
- Checkpoint: ask them to explain, in their own words, where the game used input, type conversion, a condition and a loop.

## Wrap-up
Summarise in 5 bullets what they learned. Ask: "Do you feel confident to move to Lesson 2, or want to revisit anything?" Only after a confident yes and all 8 modules recorded, mark Lesson 1 `completed` via `python-training-progress`, and hand control back to the Python Mentor to start Lesson 2.
