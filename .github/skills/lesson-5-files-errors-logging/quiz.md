# Lesson 5 – Graded Quiz Bank (3 questions)

> FOR THE FINAL QUIZ ONLY. Do not open, quote or hint at this file during teaching. Do not reveal answers before the learner answers.

## L5-Q1 (multiple choice, 1 point)
`notes.txt` already contains three lines. You run:

```python
with open("notes.txt", "w") as f:
    f.write("new")
```

What does the file contain afterwards?

A) The original three lines followed by `new`
B) Only `new`
C) The program raises an error because the file exists
D) The file is unchanged

**Answer: B.** Mode `"w"` truncates the file. Use `"a"` to append.

## L5-Q2 (predict the output, 1 point)
What is printed, in order?

```python
def f():
    try:
        return int("abc")
    except ValueError:
        print("bad")
        return -1
    finally:
        print("done")

print(f())
```

A) `bad`, `-1`
B) `bad`, `done`, `-1`
C) `done`, `bad`, `-1`
D) `ValueError` traceback

**Answer: B.** The `except` prints `bad`, the `finally` block runs before the function actually returns (printing `done`), and then `print(f())` prints `-1`.

## L5-Q3 (multiple choice, 1 point)
A program uses `import logging` with NO configuration at all, then calls `logging.debug(...)`, `logging.info(...)`, `logging.warning(...)` and `logging.error(...)` once each. Which messages appear?

A) All four
B) Only `warning` and `error`
C) Only `error`
D) None, logging needs `basicConfig` first

**Answer: B.** The default level of the root logger is WARNING, so only WARNING and above are shown.
