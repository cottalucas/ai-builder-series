# task-list.md
# Chapter 3 — Prioritised Execution Tasks
# ─────────────────────────────────────────────────────
# This is the live task layer. Your AI builder reads this to know what to build.
# Keep it short. Max 10 tasks at a time. Anything outside the top 10 doesn't belong here.
# Rule: your AI builder updates task status after every completed task, before moving on.
# ─────────────────────────────────────────────────────
# Notion: https://www.notion.so/31d26a42061181eba81fd97093010d90

---

## Current focus

What we're building this sprint:
*e.g. Ship the PDF export feature and fix the retry flow on failed analyses.*

Sprint ends: *e.g. 2026-03-22*

---

## Task format

*Use this exact format for every task. Your AI builder reads acceptance criteria as the definition of done.*

```markdown
## Task [N]: [Name]
Status: [ ] Not started / [~] In progress / [x] Done
Depends on: Task [N-1] (or "none")

What to build:
[Plain English. What must exist when this task is done. Not how to build it.]

Acceptance criteria:
- [ ] [Observable outcome — what the user sees or what the test confirms]
- [ ] [Observable outcome]
- [ ] [Observable outcome]

Files likely affected:
[List the files your AI builder will probably touch]
```

---

## In progress *(max 3 at a time)*

## Task 4: Export review as PDF
Status: [~] In progress
Depends on: Task 3

What to build:
After the review renders, a "Download PDF" button generates a clean PDF summary. The PDF contains: product name, date, all deduction cards with full fields, and the summary line. No app chrome beyond the product name.

Acceptance criteria:
- [ ] "Download PDF" button appears below the review cards
- [ ] Clicking generates and downloads a PDF without page reload
- [ ] PDF contains all deduction cards: name, status, claimed CHF, recommended CHF, delta, reasoning, form reference
- [ ] PDF contains the summary line from the AI output
- [ ] Filename: `[product-name]-review-YYYY-MM-DD.pdf`
- [ ] Works on Chrome, Safari, Firefox

Files likely affected:
- components/ReviewExport.tsx (new)
- app/review/[id]/page.tsx (add button)
- lib/pdf.ts (new — PDF generation)

---

## Up next *(ordered by priority)*

## Task 5: Retry flow on failed analysis
Status: [ ] Not started
Depends on: none

What to build:
When analysis fails, user sees a retry option. Retry reuses the existing uploaded document — no re-upload required. If retry also fails, user sees a message that the document is saved and they can try later.

Acceptance criteria:
- [ ] Failed analysis shows: "Analysis unavailable — please try again." with Retry button
- [ ] Retry triggers new analysis call without re-uploading the document
- [ ] Loading state shows during retry
- [ ] If retry succeeds: review renders normally
- [ ] If retry fails again: "Still having trouble. Your document is saved — try again in a few minutes." No second retry button.
- [ ] Document preserved in storage regardless of retry outcome

Files likely affected:
- app/review/[id]/page.tsx
- app/api/analyse/route.ts
- components/ReviewError.tsx (new or update)

---

## Task 6: *e.g. Saved review history*
Status: [ ] Not started
Depends on: Task 1 (auth)

What to build:
*e.g. Authenticated users see their previous reviews on the dashboard, newest first. Each row shows: date, filename, deduction count, status. Clicking opens the full review.*

Acceptance criteria:
- [ ] *e.g. Dashboard shows all reviews for logged-in user, newest first*
- [ ] *e.g. Each row: date, filename, deductions flagged count, status badge*
- [ ] *e.g. Clicking a row navigates to /review/[id]*
- [ ] *e.g. Empty state if no reviews: "No reviews yet." + upload button*

Files likely affected: *e.g. app/dashboard/page.tsx, components/ReviewList.tsx*

---

## Blocked

| Task | Blocked by | What needs to happen |
|---|---|---|
| *e.g. T006* | *e.g. Supabase RLS policy not written* | *e.g. Write and test RLS policy first* |

---

## Done this sprint

| Task | Completed | Notes |
|---|---|---|
| *e.g. T001 — Auth flow* | *2026-03-14* | *Sign-up, email verify, login working. Session persists on refresh.* |
| *e.g. T002 — Upload zone* | *2026-03-15* | *PDF upload working. Type + size validation working.* |
| *e.g. T003 — Review display* | *2026-03-17* | *Cards render from JSON. Status colours correct. Form refs in monospace.* |
