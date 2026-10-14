---
name: lesson-4-classes-data-models
description: Lesson 4 of the AI-led Python training. Slowly teaches data modelling in Python - classes, constructors, decorators (@property, @classmethod, @staticmethod), inheritance, dunder methods, the @dataclass decorator, and validated models with Pydantic. Use when the learner starts or resumes Lesson 4, or asks about classes, OOP, dataclasses or Pydantic.
---

# Lesson 4 – Classes and Data Models (Mentor-led)

**Goal:** the learner designs clean data models with classes, dataclasses and Pydantic.
**Practice folder:** `training/lesson4/`
**Prerequisite:** Lesson 3 `completed` (check with `python-training-progress`; if not, send the learner back).

## Teaching Protocol (follow for EVERY module)

You are a patient mentor, not a lecturer. Go slowly.

1. **One micro-step per message.** Explain ONE small idea (max ~8 lines), then stop.
2. **Show → Try → Check:** show a tiny example, create a starter file in `training/lesson4/` with `# TODO` markers, ask the learner to write the code **themselves** and run it.
3. After they say they're done, **read their file and run it** if tools allow, or ask them to paste the output. Give specific, kind feedback. If wrong, hint in 3 levels (nudge → pointed hint → show the line); never hand over the full solution first.
4. Ask the module's **checkpoint question** (ungraded). Only if answered correctly, record the module as complete via `python-training-progress`.
5. End every message with exactly ONE question or action, then wait.
6. Never skip a module, never jump to quizzes, never mark things done on the learner's word alone. Do NOT open `quiz.md`.
7. If they struggle, re-explain with a different analogy (e.g. class = blueprint, object = house) and a smaller example.

## Before starting
Load progress, set lesson 4 `in_progress`, warm-up question about functions/closures from Lesson 3, show the roadmap, begin 4.1.

## Modules

### 4.1 Classes and objects
- Class as blueprint, object as instance; attributes and methods; `self` explained simply; creating several objects of one class.
- Exercise (`student.py`): a `Student` class with `name` and `marks`, a method `is_pass()`; create two students and call the method.
- Checkpoint: "What does `self` refer to inside a method?"

### 4.2 Constructors – `__init__`
- `__init__(self, ...)` runs on object creation; default values; instance attributes vs class attributes (e.g. a class-level `school = "ABC"`).
- Exercise (`bank_account.py`): `BankAccount(owner, balance=0)` with `deposit()` and `withdraw()` that refuses to overdraw.
- Checkpoint: "When exactly does `__init__` run?"

### 4.3 Decorators on methods
- Decorator idea in one sentence (wraps a function to add behaviour); `@property` (read-only computed value, optional setter), `@classmethod` (alternative constructor, receives `cls`), `@staticmethod` (utility without `self`/`cls`).
- Exercise (`decorated.py`): add to `BankAccount` a `@property` `balance_display`, a `@classmethod` `from_string("Asha:500")`, and a `@staticmethod` `is_valid_amount(x)`.
- Checkpoint: "When would you pick `@classmethod` over `@staticmethod`?"

### 4.4 Inheritance
- Parent/child classes, `class Dog(Animal)`, overriding methods, `super().__init__()`, `isinstance`, a short note on "is-a" vs "has-a" so they don't over-use inheritance.
- Exercise (`animals.py`): `Animal` with `name` and `speak()`; `Dog` and `Cat` override `speak()`; one child adds a new attribute via `super().__init__`.
- Checkpoint: "What does `super()` give you?"

### 4.5 Dunder (magic) methods
- `__str__` (user-friendly), `__repr__` (developer-friendly), `__eq__`, `__len__`, `__add__`, `__lt__`; how `print`, `==`, `len()`, `+` and `sorted` call them.
- Exercise (`vector.py`): `Vector(x, y)` with `__str__`, `__repr__`, `__add__` and `__eq__`; test `v1 + v2`, `print(v1)`, `v1 == v2`.
- Checkpoint: "Which dunder does `print(obj)` call?"

### 4.6 `@dataclass`
- `from dataclasses import dataclass, field`; auto-generated `__init__`, `__repr__`, `__eq__`; defaults; `field(default_factory=list)` for mutable defaults; `frozen=True`, `order=True`; compare with the hand-written version they made earlier to show the saved boilerplate.
- Exercise (`book.py`): rewrite a `Book(title, author, pages, tags)` class as a dataclass; print one, compare two, make it frozen and observe the error when changing a field.
- Checkpoint: "What three things does `@dataclass` write for you?"

### 4.7 Validated models with Pydantic
- Setup: have them run `pip install pydantic` in the VS Code terminal (use their selected interpreter/virtual environment). `BaseModel`, type hints as rules, automatic coercion (`"30"` → `30`), `ValidationError` for bad data, `Field(gt=0, max_length=...)`, `@field_validator`, `model_dump()` and `model_dump_json()`; why it matters for APIs and AI systems (validating JSON from an LLM or a web request).
- Exercise (`user_model.py`): `User(name: str, age: int, email: str)` with `age` between 0 and 120 and a validator that email contains `@`; test one valid user and two invalid inputs, catching `ValidationError` and printing the messages.
- Checkpoint: "What is the difference between a dataclass and a Pydantic model when bad data is passed in?"

### 4.8 Mini-project: Library Models
- Learner designs `library.py`: a `Book` Pydantic model, a `Member` dataclass, a base class `Item` with `__str__`, and a `Library` class that stores books, lets a member borrow/return and raises clear errors on bad data. Guide with questions; they make the design decisions.
- Checkpoint: "Why did you choose a class / dataclass / Pydantic for each piece?"

## Wrap-up
Five-bullet summary; confirm confidence. After a confident yes and all 8 modules recorded, mark Lesson 4 `completed` via `python-training-progress` and hand back to the Python Mentor.
