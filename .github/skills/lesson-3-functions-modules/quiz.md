# Lesson 3 – Graded Quiz Bank (3 questions)

> FOR THE FINAL QUIZ ONLY. Do not open, quote or hint at this file during teaching. Do not reveal answers before the learner answers.

## L3-Q1 (multiple choice, 1 point)
What does this print?

```python
def show(*args, **kwargs):
    print(len(args), len(kwargs))

show(1, 2, x=3, y=4, z=5)
```

A) `5 0`
B) `2 3`
C) `3 2`
D) It raises an error

**Answer: B.** `1, 2` go into the `args` tuple (2 items); `x, y, z` go into the `kwargs` dict (3 items).

## L3-Q2 (predict the output, 1 point)
What does this print?

```python
def make_multiplier(n):
    def multiply(x):
        return x * n
    return multiply

double = make_multiplier(2)
triple = make_multiplier(3)
print(double(5), triple(5))
```

A) `10 10`
B) `15 15`
C) `10 15`
D) `5 5`

**Answer: C.** Each returned function is a closure that remembers its own `n` (2 and 3).

## L3-Q3 (write code, up to 1 point)
Given `nums = [1, 2, 3, 4, 5, 6]`, write ONE expression that uses `map`, `filter` and `lambda` to produce a list of the squares of only the even numbers: `[4, 16, 36]`.

**Scoring rubric**
- 1 point: uses `filter` with a lambda for evenness AND `map` with a lambda for squaring, wrapped in `list()`, correct result. Order may be nested either way as long as the result is right (a list comprehension alone gets 0.5).
- 0.5 point: right idea with one small slip (missing `list()`, wrong operator) or a correct list comprehension that does not use `map`/`filter`.
- 0 points: no working approach.

Example full-credit answer:
```python
result = list(map(lambda x: x * x, filter(lambda x: x % 2 == 0, nums)))
```
