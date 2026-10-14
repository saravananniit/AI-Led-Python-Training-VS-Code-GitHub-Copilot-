# Lesson 1 – Graded Quiz Bank (3 questions)

> FOR THE FINAL QUIZ ONLY. Do not open, quote or hint at this file during teaching. Do not reveal answers before the learner answers.

## L1-Q1 (multiple choice, 1 point)
What happens when this program runs and the user types `25`?

```python
age = input("Age: ")
print(age + 1)
```

A) Prints `26`
B) Prints `251`
C) Raises a `TypeError`
D) Prints `25+1`

**Answer: C.** `input()` returns a string, and a `str` cannot be added to an `int`. Fix: `int(age) + 1`.

## L1-Q2 (predict the output, 1 point)
What does this print?

```python
total = 0
for i in range(1, 6):
    if i % 2 == 0:
        continue
    total += i
print(total)
```

**Answer: 9.** `continue` skips the even numbers, so it adds 1 + 3 + 5. (Give 0 for any other answer.)

## L1-Q3 (write code, up to 1 point)
Write code that asks the user for a score (a whole number from 0 to 100) and prints `Distinction` if it is 90 or more, `Pass` if it is 40 or more, otherwise `Fail`.

**Scoring rubric**
- 1 point: converts the input with `int()`, uses `if / elif / else` in a correct order (highest threshold first), prints the right words.
- 0.5 point: logic is right but input is not converted, or there is a small syntax slip, or the branch order produces wrong results for some scores.
- 0 points: missing decision logic or wrong approach.

Example full-credit answer:
```python
score = int(input("Score: "))
if score >= 90:
    print("Distinction")
elif score >= 40:
    print("Pass")
else:
    print("Fail")
```
