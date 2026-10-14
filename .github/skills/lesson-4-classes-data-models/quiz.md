# Lesson 4 – Graded Quiz Bank (3 questions)

> FOR THE FINAL QUIZ ONLY. Do not open, quote or hint at this file during teaching. Do not reveal answers before the learner answers.

## L4-Q1 (multiple choice, 1 point)
What does the `@dataclass` decorator automatically generate for a class?

A) `__init__`, `__repr__` and `__eq__`
B) Only `__init__`
C) A database table for the class
D) Runtime type checking of every field

**Answer: A.** Dataclasses remove boilerplate, but they do NOT validate types at runtime (D is wrong; that is what Pydantic does).

## L4-Q2 (predict the output, 1 point)
What does this print?

```python
class Animal:
    def __init__(self, name):
        self.name = name
    def __str__(self):
        return f"Animal({self.name})"

class Dog(Animal):
    def __str__(self):
        return "Dog:" + super().__str__()

print(Dog("Rex"))
```

A) `Animal(Rex)`
B) `Dog:Rex`
C) `Dog:Animal(Rex)`
D) `<__main__.Dog object at ...>`

**Answer: C.** `print` calls `__str__`; `Dog.__str__` calls the parent's `__str__` via `super()` and adds a prefix.

## L4-Q3 (multiple choice, 1 point)
Using Pydantic v2, what happens here?

```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int

u = User(name="Asha", age="abc")
```

A) `age` becomes `0`
B) `age` stays the string `"abc"`
C) A `ValidationError` is raised
D) `age` silently becomes `None`

**Answer: C.** `"abc"` cannot be converted to `int`, so Pydantic raises `ValidationError`. (Note: `"30"` WOULD be coerced to `30`.)
