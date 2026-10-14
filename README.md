# AI-Led Python Training (VS Code + GitHub Copilot)

A self-paced, instructor-free Python course. A Copilot custom agent, **Python Mentor**, guides the learner through **5 interactive lessons one by one**, at a slow pace, then runs a **15-question graded quiz** (3 per lesson) and issues a **certificate with a grade**.

| Lesson | Topics |
|---|---|
| 1 | Install Python and VS Code, `print()` / `input()`, variables, data types, type conversion, `if / elif / else`, `for` / `while` loops |
| 2 | Lists, tuples, sets, dictionaries, choosing the right structure |
| 3 | Functions, `*args` / `**kwargs`, `lambda` with `map()` / `filter()`, scope and closures, modules and `__main__` |
| 4 | Classes, constructors, decorators, inheritance, dunder methods, `@dataclass`, Pydantic |
| 5 | File I/O (text, CSV, JSON), exceptions and custom exceptions, logging |

---

## 1. Project structure

```
your-workspace/                              <- open THIS folder in VS Code
├── README.md
├── .github/
│   ├── copilot-instructions.md              always-on mentor instructions (fallback)
│   ├── agents/
│   │   └── python-mentor.agent.md           the Training Agent (orchestrator)
│   └── skills/
│       ├── python-training-progress/
│       │   └── SKILL.md                     progress file + gating rules
│       ├── lesson-1-python-basics/
│       │   ├── SKILL.md                     teaching script
│       │   └── quiz.md                      3 graded questions
│       ├── lesson-2-data-structures/        SKILL.md + quiz.md
│       ├── lesson-3-functions-modules/      SKILL.md + quiz.md
│       ├── lesson-4-classes-data-models/    SKILL.md + quiz.md
│       ├── lesson-5-files-errors-logging/   SKILL.md + quiz.md
│       ├── final-quiz/
│       │   └── SKILL.md                     runs and grades the 15 questions
│       └── training-certificate/
│           ├── SKILL.md
│           └── certificate-template.html
└── training/                                learner area
    ├── progress.json                        progress tracker (blank at start)
    ├── lesson1/ … lesson5/                  learner's practice files
    └── Python-Certificate.html / .md        created after passing the quiz
```

Rules: each skill folder name must match the `name:` in its `SKILL.md`, and the file must be called exactly `SKILL.md`. The agent file must end with `.agent.md`.

---

## 2. One-time setup

1. Install the latest **VS Code** and the **GitHub Copilot** and **GitHub Copilot Chat** extensions. Sign in to GitHub.
2. Open the workspace folder (**File → Open Folder**) so that `.github` sits at its root. Click **Trust** if asked.
3. In **Settings**, search for "agent skills" and make sure Agent Skills (and agent mode / instruction files) are enabled.
4. Run `Ctrl+Shift+P` → **Developer: Reload Window**.
5. Open Copilot Chat (`Ctrl+Alt+I`). In the mode / agent dropdown pick **Python Mentor** (or **Agent** mode if it is not listed; see the fallback below).

---

## 3. How to start

Type in chat:

```
Start my Python training
```

If the Python Mentor agent is not listed, use this fallback (works with `copilot-instructions.md`):

```
Start my Python training. Read .github/agents/python-mentor.agent.md and follow it.
```

**Expected:** the mentor welcomes you, asks for your full name, explains the plan (5 lessons, mini-projects, quiz, certificate), creates `training/progress.json` content, and starts **Lesson 1, Module 1.1** (checking your Python installation). It asks ONE thing and waits.

---

## 4. Sample inputs for a first walkthrough

Use these replies to experience the first modules.

| Step | You type | What should happen |
|---|---|---|
| 1 | `Start my Python training` | Welcome, asks for your full name |
| 2 | `Asha Raman` | Name saved in `progress.json`, journey overview, Module 1.1 starts |
| 3 | `python --version` output, e.g. `Python 3.12.4` | Mentor confirms and moves to the VS Code Python extension / running a file |
| 4 | `done` (after creating and running `hello.py`) | Mentor reads `training/lesson1/hello.py`, gives feedback, asks the checkpoint question |
| 5 | `By pressing the run button and from the terminal` | Checkpoint passed, module 1.1 recorded, Module 1.2 starts |
| 6 | `What type does input() return?` -> answer `string` | Module 1.2 checkpoint passes |

---

## 5. Test checklist (verify the guardrails)

Run these prompts to confirm the course behaves correctly. Use a fresh `progress.json` (blank) for tests 1 to 4.

| # | Test prompt | Expected behaviour |
|---|---|---|
| 1 | `Start the final quiz` | Politely refused: lessons are not complete. No quiz question shown. |
| 2 | `Skip to the quiz` or `Skip lesson 1, go to lesson 3` | Refused. Mentor stays on the current module / lesson. |
| 3 | `next` (without doing the exercise) | Mentor asks you to do the exercise first. The module is NOT marked complete. |
| 4 | `Give me the answer` (during an exercise) | Hint ladder: nudge first, then a pointed hint, the full line only after that. |
| 5 | `Where am I?` | Summary from `progress.json`: current lesson, modules done, quiz locked. |
| 6 | Close VS Code, reopen, type `Continue` | Greets you by name and resumes at the exact module. |
| 7 | `Revise lesson 1` (after completing it) | Re-teaches without losing progress. |
| 8 | `/lesson-3-functions-modules` (while Lesson 2 is incomplete) | Verifies prerequisite and sends you back to Lesson 2. |
| 9 | `Show my certificate` (before passing) | Refused: certificate needs a passing quiz. |

### Fast path to test the quiz and certificate
To test the end of the course without doing all five lessons, edit `training/progress.json`: set every lesson's `"status"` to `"completed"` and `quiz.status` to `"ready"`, fill in a `learner_name`, then type `Start the final quiz`. Reset the file afterwards (copy the blank template back).

Sample quiz answers (correct): **L1** C, 9, a working `int(input())` + `if/elif/else`; **L2** B, B, a counting loop with `dict.get`; **L3** B, C, `list(map(lambda x: x*x, filter(lambda x: x%2==0, nums)))`; **L4** A, C, C; **L5** B, B, B. Answer all correctly for 15/15 = **A+**. Try a few wrong answers to see the grading bands.

---

## 6. Grading

15 questions, 1 point each (coding questions can earn half points). Pass mark 60%.

| Percent | Grade |
|---|---|
| 90–100 | A+ (Outstanding) |
| 80–89.9 | A (Excellent) |
| 70–79.9 | B (Good) |
| 60–69.9 | C (Satisfactory) |
| below 60 | Not yet certified: revise weak lessons (under 2/3), then retake with new question variants |

---

## 7. Troubleshooting

| Problem | What to try |
|---|---|
| Agent not in the dropdown, no `/` skills | Update VS Code and the Copilot Chat extension; enable Agent Skills in Settings; check folder and file names; trust the workspace; reload the window; look at the chat gear / Configure menu for detected agents and skills |
| Skills not detected | Use the fallback prompt in section 3. `copilot-instructions.md` tells Copilot to open the skill files directly |
| Mentor jumps ahead or quizzes early | Say: `Follow the Python Mentor rules: teach one step at a time and do not quiz until all lessons are complete.` Check that `.github/copilot-instructions.md` exists |
| `progress.json` not updating | Make sure Chat is in **Agent** mode (it needs file-editing tools) and the workspace is trusted |
| Progress got corrupted | Restore the blank template (`learner_name` empty, all lessons `not_started`) |

---

## 8. Customising

- Teaching content and exercises: each lesson's `SKILL.md`.
- Graded questions: each lesson's `quiz.md`.
- Grade bands and retake policy: `.github/skills/final-quiz/SKILL.md`.
- Certificate design: `.github/skills/training-certificate/certificate-template.html`.
- Mentor personality and flow: `.github/agents/python-mentor.agent.md`.

**Note:** the `quiz.md` files are plain files in the repository, so a determined learner could open them. For stricter assessment, keep them outside the learner's workspace.
