# Lesson 2 – Graded Quiz Bank (3 questions)

> FOR THE FINAL QUIZ ONLY. Do not open, quote or hint at this file during teaching. Do not reveal answers before the learner answers.

## L2-Q1 (multiple choice, 1 point)
What does this print?

```python
nums = [10, 20, 30, 40, 50]
print(nums[1:4])
```

A) `[10, 20, 30, 40]`
B) `[20, 30, 40]`
C) `[20, 30, 40, 50]`
D) `[10, 20, 30]`

**Answer: B.** The start index is included, the stop index is excluded.

## L2-Q2 (multiple choice, 1 point)
Given these two lines, which statement is TRUE?

```python
t = (1, 2, 3)
s = {1, 2, 2, 3}
```

A) `t[0] = 10` changes the first item of the tuple
B) `len(s)` is `3`
C) `s[0]` returns `1`
D) `t.append(4)` adds an item to the tuple

**Answer: B.** Sets drop duplicates. Tuples are immutable (A, D fail) and sets have no indexing (C fails).

## L2-Q3 (write code, up to 1 point)
Given `words = ["a", "b", "a", "c", "b", "a"]`, write code that builds a dictionary counting how many times each word appears. The result should be `{'a': 3, 'b': 2, 'c': 1}`.

**Scoring rubric**
- 1 point: correct approach (loop + `dict.get(w, 0) + 1`, or `if w in d` / else, or `collections.Counter` / `defaultdict`) that would produce the right result.
- 0.5 point: right idea but a bug that would stop it working (e.g. updating a missing key without initialising it, wrong variable) or only partial logic.
- 0 points: no dictionary-based counting.

Example full-credit answer:
```python
counts = {}
for w in words:
    counts[w] = counts.get(w, 0) + 1
print(counts)
```
