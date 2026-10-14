---
name: final-quiz
description: Runs the graded final quiz for the AI-led Python training - 15 questions (3 per lesson, Lessons 1-5), one at a time, scored and graded. Use ONLY after all five lessons are completed in training/progress.json, when the learner asks to take the final quiz or retake it.
---

# Final Quiz – 15 Questions, 5 Lessons

## Step 0 – Gate check (mandatory)
1. Load `training/progress.json` via the `python-training-progress` skill.
2. If ANY lesson is not `completed`, **stop**. Do not read any `quiz.md`. Tell the learner kindly which lesson is pending and offer to continue it.
3. If all five are `completed`, set `quiz.status` to `ready` (if not already) and continue.

## Step 1 – Brief the learner
Explain in a few lines: 15 questions, 3 from each lesson, 1 point each (coding questions may earn half points), one question at a time, no hints and no looking things up during the quiz, a short explanation after each answer. Passing mark is 60%. Ask "Ready to begin?" and wait.

## Step 2 – Load the question bank
Read these five files (only now):
- `.github/skills/lesson-1-python-basics/quiz.md`
- `.github/skills/lesson-2-data-structures/quiz.md`
- `.github/skills/lesson-3-functions-modules/quiz.md`
- `.github/skills/lesson-4-classes-data-models/quiz.md`
- `.github/skills/lesson-5-files-errors-logging/quiz.md`

Ask the questions in lesson order: L1-Q1, L1-Q2, L1-Q3, L2-Q1 … L5-Q3. Set `quiz.status` to `in_progress` and increment `quiz.attempt` on a fresh start.

## Step 3 – Ask one question at a time
For each question:
1. Show "Question N of 15 – Lesson X" and the question text with its code block. For multiple-choice, show the options; for write-code questions, tell them to type their code in the chat (or in `training/quiz_answer.py` and say "done").
2. **Wait for the answer.** Never reveal the answer key beforehand.
3. Score using the answer or rubric in that lesson's quiz file. Be strict but fair; accept equivalent correct code.
4. Reply with: ✅ / ❌ / 🟡 (half credit), the points earned, and a 2–3 line explanation including the correct answer. No re-attempts.
5. Save to `quiz.answers` (question id, learner answer summary, points) and update `quiz.current_question` via `python-training-progress` so the quiz can resume if interrupted.
6. Then ask: "Next question?" or simply continue to the next one when the learner confirms.

If the learner asks for a hint or the answer mid-quiz, kindly decline: "Quiz mode – let's keep it fair; we'll go through everything at the end."

## Step 4 – Score and grade
Total = sum of points (max 15). Percent = total / 15 × 100, rounded to one decimal. Per-lesson score = points for its 3 questions (0–3).

| Percent | Grade | Result |
|---|---|---|
| 90 – 100 | **A+** (Outstanding) | Certified |
| 80 – 89.9 | **A** (Excellent) | Certified |
| 70 – 79.9 | **B** (Good) | Certified |
| 60 – 69.9 | **C** (Satisfactory) | Certified |
| below 60 | **Not yet certified** | Revise and retake |

Save `scores`, `total`, `percent`, `grade` in the progress file and set `quiz.status` to `completed`.

## Step 5 – Results report
Present a short table: lesson, score out of 3, and a strength/needs-revision label (needs revision if below 2 out of 3). Then the total, percent and grade. Give 2–3 sentences of personal, encouraging feedback naming their strongest lesson and the one to revisit.

## Step 6 – Next action
- **Certified (≥ 60%)** → hand over to the `training-certificate` skill to issue the certificate. Mention which lessons (if any) are worth revising anyway.
- **Not certified (< 60%)** → do NOT issue a certificate. Offer a focused revision of every lesson scoring under 2/3 (re-teach only the weak modules, using that lesson's skill, with fresh examples). When they are ready, run a **retake** of only those lessons' questions, using **new equivalent variants** you write (same concept and difficulty, different names/values; never reuse the original wording). Keep the points from lessons already passed, recompute the total, increment `quiz.attempt`, and re-grade with the same table. Record the attempt number on the certificate if one is later issued.
