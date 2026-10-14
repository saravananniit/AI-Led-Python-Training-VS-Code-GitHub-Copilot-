---
name: python-training-progress
description: Reads, creates and updates the learner's progress file (training/progress.json) for the AI-led Python training. Use at the start of every training session to resume, and whenever a module, lesson, quiz or certificate state changes. Enforces the gating rules that stop lessons from being skipped.
---

# Python Training – Progress & Gating

The single source of truth for where the learner is lives in **`training/progress.json`** in the workspace root. Never rely on chat memory alone.

## 1. Session start (always)

1. Look for `training/progress.json`.
   - **Missing, or present with an empty `learner_name`** → this is a new learner. Ask for their **full name** (it goes on the certificate), then create (or fill in) the file from the template below and make sure the folders `training/lesson1` … `training/lesson5` exist.
   - **Present with a name** → read it, greet the learner by name, tell them in one or two sentences where they stopped ("Lesson 2, module 2.4 – traversing lists"), and ask if they want to continue from there.
2. Never restart a lesson that is `completed` unless the learner explicitly asks to revise it.

## 2. File template

```json
{
  "learner_name": "",
  "started_at": "YYYY-MM-DD",
  "current_lesson": 1,
  "lessons": {
    "1": { "status": "not_started", "modules_completed": [], "completed_at": null },
    "2": { "status": "not_started", "modules_completed": [], "completed_at": null },
    "3": { "status": "not_started", "modules_completed": [], "completed_at": null },
    "4": { "status": "not_started", "modules_completed": [], "completed_at": null },
    "5": { "status": "not_started", "modules_completed": [], "completed_at": null }
  },
  "quiz": {
    "status": "locked",
    "attempt": 0,
    "current_question": 0,
    "scores": { "1": null, "2": null, "3": null, "4": null, "5": null },
    "total": null,
    "percent": null,
    "grade": null,
    "answers": []
  },
  "certificate": { "issued": false, "id": null, "issued_at": null }
}
```

`status` values for a lesson: `not_started`, `in_progress`, `completed`.
`status` values for the quiz: `locked`, `ready`, `in_progress`, `completed`.

## 3. Gating rules (hard rules – never bend them)

1. **Teach before you test.** A module may be added to `modules_completed` only AFTER the learner has (a) been taught the concept step by step, (b) done the hands-on exercise themselves, and (c) answered the module checkpoint correctly.
2. **A lesson becomes `completed` only when every module of that lesson is in `modules_completed`** and the learner has finished the lesson's mini-project and confirmed they feel ready to move on.
3. **Lessons are sequential.** Lesson N+1 cannot start until lesson N is `completed`.
4. **The quiz is `locked` until all 5 lessons are `completed`.** Then set it to `ready`. Never show, hint at, or ask quiz questions before that, and never open any `quiz.md` file during a lesson.
5. **The certificate** may only be issued when `quiz.status` is `completed` and `quiz.percent` is 60 or higher.
6. Update the file **immediately** after each gate is passed (not in batches), then continue. Keep the JSON valid.
7. Never tell the learner a module is done "to be nice". If the exercise or checkpoint was not done, say so kindly and do it first.

## 4. Updating

- Use targeted edits to the JSON file. After editing, re-read it if you are unsure it is still valid JSON.
- When a lesson starts: `status` → `in_progress`, `current_lesson` → N.
- When a module passes: append its id (e.g. `"2.4"`) to `modules_completed`.
- When a lesson finishes: `status` → `completed`, set `completed_at`, set `current_lesson` to N+1 (or stay 5 if last), and if it was lesson 5 set `quiz.status` to `ready`.
