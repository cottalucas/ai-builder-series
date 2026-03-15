# PROGRESS.md
# The agent writes here after every completed task.
# This is the memory between sessions — without it, every session starts from zero.
#
# RULE FOR AGENT: After every completed task, add a line here before moving to the next.
# FORMAT: [date] · [task] · [status] · [what was built] · [next]

---

## Current state

Phase: *Prototype / Product / Growth*
Last updated: *YYYY-MM-DD*
Working: *e.g. Auth + upload + review display end-to-end*
Blocked: *e.g. PDF export — waiting on library decision*
Next session: *e.g. T004 PDF export, then T005 retry flow*

---

## Chapter 1

| File | Status |
|---|---|
| .cursor/rules/project.md | [ ] / [~] / [x] |
| .cursor/rules/stack.md | [ ] / [~] / [x] |
| chapter-1/the-brief.md | [ ] / [~] / [x] |
| chapter-1/SPEC.md | [ ] / [~] / [x] |
| chapter-1/VALIDATION.md | [ ] / [~] / [x] |
| ENV.md | [ ] / [~] / [x] |

Exit: *5+ real users completed the core flow without help. Genuine value observed.*

---

## Chapter 2

| File | Status |
|---|---|
| chapter-2/PRD.md | [ ] / [~] / [x] |
| chapter-2/GO-LIVE.md | [ ] / [~] / [x] |
| chapter-2/ARCHITECTURE.md | [ ] / [~] / [x] |
| chapter-2/SCENARIOS.md | [ ] / [~] / [x] |
| chapter-2/user-journeys.md | [ ] / [~] / [x] |
| chapter-2/design-brief.md | [ ] / [~] / [x] |

Exit: *Product passes acceptance criteria. Metrics instrumentation live before launch.*

---

## Chapter 3

| File | Status |
|---|---|
| chapter-3/LAUNCH.md | [ ] / [~] / [x] |
| chapter-3/task-list.md | [ ] / [~] / [x] |
| chapter-3/implementation-plan.md | [ ] / [~] / [x] |

---

## Task log *(agent writes here — newest first)*

```
[date] · [task ID] · [task name] · complete
  Built: [1–2 sentences]
  Tests: [N passed, N failed]
  Next: [next task]
```

Example:
```
2026-03-17 · T003 · Review display · complete
  Built: ReviewCard renders deductions from JSON. Status badges working. Form refs in monospace.
  Tests: 8 passed, 0 failed
  Next: T004 — PDF export

2026-03-15 · T002 · Upload zone · complete
  Built: Drag-drop + file picker. Type/size validation client-side. Progress bar. Error states.
  Tests: 6 passed, 0 failed
  Next: T003 — Review display
```

---

## Decisions log

| Date | Decision | Why |
|---|---|---|
| *e.g. 2026-03-14* | *e.g. pdf-parse over OCR* | *e.g. Lower latency, lower cost. Most Swiss digital docs have text layers.* |
