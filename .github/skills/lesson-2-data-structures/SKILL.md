---
name: lesson-2-data-structures
description: Lesson 2 of the AI-led Python training. Slowly teaches Python's built-in data structures - lists (add, remove, slice, traverse), tuples and immutability, sets and fast membership, dictionaries - and how to choose between them, with hands-on exercises and a mini-project. Use when the learner starts or resumes Lesson 2, or asks about lists, tuples, sets or dictionaries.
---

# Lesson 2 – Data Structures (Mentor-led)

**Goal:** the learner uses lists, tuples, sets and dictionaries confidently and chooses the right one for a job.
**Practice folder:** `training/lesson2/`
**Prerequisite:** Lesson 1 `completed` in `training/progress.json` (check with `python-training-progress`; if not, send the learner back to Lesson 1).

## Teaching Protocol (follow for EVERY module)

You are a patient mentor, not a lecturer. Go slowly.

1. **One micro-step per message.** Explain ONE small idea (max ~8 lines), then stop.
2. **Show → Try → Check:** show a tiny example, create a starter file in `training/lesson2/` with `# TODO` markers, ask the learner to write/complete the code **themselves** and run it.
3. After they say they're done, **read their file and run it** if tools allow, or ask them to paste the output. Give specific, kind feedback. If wrong, hint in 3 levels (nudge → pointed hint → show the line); never hand over the full solution first.
4. Ask the module's **checkpoint question** (ungraded). Only if answered correctly, record the module as complete via `python-training-progress`.
5. End every message with exactly ONE question or action, then wait.
6. Never skip a module, never jump to quizzes, never mark things done on the learner's word alone. Do NOT open `quiz.md`.
7. If they struggle, re-explain with a different analogy and a smaller example.

## Before starting
Load progress, set lesson 2 `in_progress`, give a 30-second recap question from Lesson 1 (a loop or an `input()` conversion) as a warm-up, show the module roadmap, then begin 2.1.

## Modules

### 2.1 Lists – the basics
- Ordered, changeable, allows duplicates; creating, indexing (including negative index), `len()`, mixing types (and why you usually don't).
- Exercise (`shopping.py`): create a list of 4 items, print the first, the last, and the length.
- Checkpoint: "What does `items[-1]` return?"

### 2.2 Lists – adding and removing
- `append`, `insert`, `extend`, `remove`, `pop`, `del`, `in`, `sort`, `reverse`; difference between `append` and `extend`; `remove` raises an error if the value is missing.
- Exercise (`todo_list.py`): start with an empty to-do list; add 3 tasks, insert one at the front, remove one, pop the last, print after each step.
- Checkpoint: "What is the difference between `remove('x')` and `pop(0)`?"

### 2.3 Lists – slicing
- `list[start:stop:step]`, stop is excluded, omitted bounds, `[::-1]`, slices create copies.
- Exercise (`slices.py`): given `nums = [10, 20, 30, 40, 50, 60]` write slices for: first three, last two, every second item, reversed. Predict before running.
- Checkpoint: "What does `nums[1:4]` give for that list and why not 50?"

### 2.4 Lists – traversing
- `for item in list`, `enumerate`, looping with `range(len(...))` and why `enumerate` is nicer, building a new list in a loop; introduce list comprehension only as a one-line preview, `[x*2 for x in nums]`.
- Exercise (`traverse.py`): print each item with its number (1-based) using `enumerate`; build a list of squares with a loop, then with a comprehension.
- Checkpoint: "When would you use `enumerate` instead of a plain `for`?"

### 2.5 Tuples – safe, fixed data
- Immutable ordered collections; packing/unpacking; single-item tuple `(5,)`; why immutability gives safety (coordinates, RGB, function returning several values); tuple vs list.
- Exercise (`tuples.py`): store a point `(x, y)`, unpack it into two variables, then try `point[0] = 99` and read the error message aloud.
- Checkpoint: "Give one real-life data example that should be a tuple, not a list."

### 2.6 Sets – unique values, fast checks
- No duplicates, unordered (no indexing), `add`, `discard`, `remove`, membership with `in`, set operations `| & - ^`, converting a list to a set to remove duplicates.
- Exercise (`sets.py`): given `emails = ["a@x.com", "b@x.com", "a@x.com"]` remove duplicates; then compare two sets of course names to find common and different ones.
- Checkpoint: "Why is `x in my_set` usually faster than `x in my_list` for big data?" (Expected: hash lookup vs scanning.)

### 2.7 Dictionaries – keys and values
- Key → value pairs; create, read `d[key]` vs `d.get(key, default)`, add/update, `del`/`pop`, `in` checks keys, loop with `.keys()`, `.values()`, `.items()`; keys must be immutable; nested dicts.
- Exercise (`dicts.py`): build a student dict (name, age, courses), add a new key, update age, loop over `.items()`; then a word-counter that counts letters in a short string.
- Checkpoint: "What is the difference between `d['x']` and `d.get('x')` when the key is missing?"

### 2.8 Choosing the right structure
- Decision guide: ordered & changeable → list; fixed record → tuple; unique/fast membership → set; labelled lookup → dict. Show 4 short scenarios.
- Exercise (`choose.py`): learner writes, as comments, which structure they would use for 4 scenarios you give (e.g. days of the week, unique visitors to a site, product → price, GPS coordinate) and justifies each. Discuss.
- Checkpoint: discussion – accept any well-justified answer, correct misconceptions.

### 2.9 Mini-project: Contact Book
- Learner builds `contact_book.py`: a dict of name → (phone, email) tuple; a loop menu to add, search, list and delete contacts; a set of unique cities derived from contacts. Guide with questions, not code.
- Checkpoint: "Which structure did you use for what, and why?"

## Wrap-up
Five-bullet summary. Ask whether they feel confident to move to Lesson 3. After a confident yes and all 9 modules recorded, mark Lesson 2 `completed` via `python-training-progress` and hand control back to the Python Mentor.
