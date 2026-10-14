---
name: training-certificate
description: Issues the graded Certificate of Completion for the AI-led Python training once the final quiz is passed (60% or higher). Use only after the final quiz is completed, or when the learner asks to see or regenerate their certificate.
---

# Training Certificate

## Gate check (mandatory)
1. Load `training/progress.json` via `python-training-progress`.
2. Issue a certificate **only if** `quiz.status` is `completed` AND `quiz.percent` ≥ 60. Otherwise explain kindly that the quiz must be passed first and offer revision (see the `final-quiz` skill).
3. If `certificate.issued` is already `true`, don't create a new ID: just re-display or regenerate the existing certificate with the same ID.

## Issue the certificate
1. Create `certificate.id` in the form `PY-YYYYMMDD-NNNN`, where the date is today and NNNN is four random digits.
2. Copy `.github/skills/training-certificate/certificate-template.html` to `training/Python-Certificate.html` and replace these placeholders:
   - `{{LEARNER_NAME}}` – learner's name from the progress file
   - `{{DATE}}` – today's date, e.g. `13 October 2026`
   - `{{GRADE}}` – `A+`, `A`, `B` or `C`
   - `{{GRADE_LABEL}}` – Outstanding / Excellent / Good / Satisfactory
   - `{{PERCENT}}` – percentage with one decimal
   - `{{TOTAL}}` – points out of 15 (e.g. `13.5`)
   - `{{L1}}` … `{{L5}}` – lesson scores out of 3
   - `{{ATTEMPT}}` – quiz attempt number
   - `{{CERT_ID}}` – the certificate ID
3. Also write a plain-text version `training/Python-Certificate.md` with the same facts, for learners who cannot open HTML.
4. Update `certificate` in the progress file: `issued: true`, `id`, `issued_at`.

## Celebrate and close
- Give the learner a warm congratulation with their name, grade and score.
- Tell them where the files are and how to view/print: right-click `training/Python-Certificate.html` → *Open with Live Server* or *Reveal in File Explorer* and open in a browser; use the browser's Print → Save as PDF.
- Offer 2–3 realistic next steps matched to the grade (e.g. build a small FastAPI app, explore `pytest`, read about async, try an LLM API project).
- Do not exaggerate: this is a self-paced training completion certificate, not an accredited qualification.
