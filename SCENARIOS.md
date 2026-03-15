# SCENARIOS.md
# Chapter 2 — Edge Cases and Holdout Scenarios
# ─────────────────────────────────────────────────────
# IMPORTANT: Keep this file in a SEPARATE repo or private folder from your main codebase.
# Your AI builder must NEVER see this file.
# If the AI writes both the code and the tests, it can make tests pass by
# confirming what it built — not what you specified. These scenarios are your
# independent verification layer. They only work if the AI has never seen them.
# ─────────────────────────────────────────────────────
# Fill this BEFORE building. Add scenarios as you discover edge cases.
# Run every scenario before every release. A failing scenario is a bug, not a missing feature.
# Notion: https://www.notion.so/31d26a420611813499bfe07c988c97ac

---

## How to run scenarios

1. Open the product in a clean browser session (no cached state)
2. For each scenario: set up the precondition, perform the action, verify the expected result
3. If the result does not match expected: that is a bug — file it before shipping
4. Mark each scenario pass/fail after every release

---

## Holdout scenarios

*Cases explicitly out of scope for this version. Named so they don't get accidentally built.*

| Scenario | Why it's a holdout | Revisit when |
|---|---|---|
| *e.g. Kanton Bern document support* | *Different rules, different form refs. Out of scope until Zürich is stable.* | *After 500 Zürich reviews* |
| *e.g. Self-employed returns* | *Completely different document set and deduction logic.* | *After product is profitable* |
| *e.g. Multi-year comparison* | *Requires storing prior-year reviews — not built yet.* | *When saved history ships* |
| *Add more* | | |

---

## Scenario format

```
## S[NNN]: [Scenario name]
Precondition: [Exact system state before the action]
Action: [What the user or system does — step by step]
Expected: [Observable outcome if the system is working correctly]
Failure: [What a broken system does instead]
Severity: CRITICAL / HIGH / MEDIUM
Status: [ ] Not tested / [x] Pass / [!] Fail
```

---

## Scenarios

## S001: Homeoffice claim above flat rate
Precondition: Upload a document with Homeoffice claim of CHF 1,800. Kanton Zürich flat rate at 120 days = CHF 360.
Action: Complete full review flow end-to-end.
Expected: Review flags as over-claimed. Shows claimed CHF 1,800, recommended CHF 360. Reasoning explains: "Kanton Zürich flat rate is CHF 3/day × 120 days = CHF 360." Cites Formular 5, Ziffer 5.1.
Failure: Review says "looks correct" without comparison. Or shows flag without CHF amounts. Or missing Formular reference.
Severity: CRITICAL
Status: [ ] Not tested

## S002: Missed 3a Säule deduction
Precondition: Upload a document with no 3a Säule deduction claimed.
Action: Complete full review flow end-to-end.
Expected: Review identifies missed 3a deduction. Shows estimated CHF value (max CHF 7,056 employed). Cites Formular 10.
Failure: 3a not mentioned. Or mentioned without CHF estimate. Or Formular reference missing.
Severity: HIGH
Status: [ ] Not tested

## S003: Non-Zürich document
Precondition: Upload a tax document from Kanton Bern.
Action: Complete full review flow.
Expected: Review flags Kanton mismatch explicitly: "This document appears to be from Kanton Bern. Analysis is optimised for Kanton Zürich — results may not apply." Does not apply Zürich-specific rules.
Failure: Review applies Zürich rules to non-Zürich document without warning.
Severity: HIGH
Status: [ ] Not tested

## S004: Scanned PDF (image-only, no text layer)
Precondition: Upload a PDF that is a scanned image with no extractable text.
Action: Attempt to analyse.
Expected: Product detects empty text extraction. Shows: "This document appears to be a scanned image. Please upload a digital PDF for best results." Does not proceed to AI call.
Failure: AI call made with empty/garbled text. AI returns hallucinated output.
Severity: HIGH
Status: [ ] Not tested

## S005: All deductions correctly claimed
Precondition: Upload a document where all deductions are correctly claimed.
Action: Complete full review flow.
Expected: Review shows positive result: "Everything looks correct. No missed or under-claimed deductions found." No empty cards, no blank screen.
Failure: Empty screen. Or error state. Or false positives shown.
Severity: MEDIUM
Status: [ ] Not tested

## S006: Wrong file type uploaded
Precondition: Attempt to upload a .jpg or .docx file.
Action: Select the file in the upload zone.
Expected: File rejected immediately with message: "Please upload a PDF file." No upload attempted. No API call made.
Failure: File upload attempted. Or no error shown. Or generic error shown.
Severity: MEDIUM
Status: [ ] Not tested

## S007: User A cannot see User B's review
Precondition: Two accounts exist — User A and User B. User B has a completed review.
Action: Log in as User A. Attempt to access User B's review URL directly (/review/[user-b-review-id]).
Expected: 404 or redirect to dashboard. User A sees no content from User B's review.
Failure: User A can see User B's review data.
Severity: CRITICAL
Status: [ ] Not tested

*Add new scenarios here as you discover edge cases in QA and production.*

---

## Error states verification

*Run these in every release. Every failure mode must show a readable message.*

| Failure | Expected user message | Pass/Fail |
|---|---|---|
| AI returns no result | "Analysis unavailable — please try again." | |
| AI returns malformed JSON | "Analysis unavailable — please try again." | |
| Upload fails (storage) | "Upload failed — please try again." | |
| File over 10MB | "File is too large. Please upload a PDF under 10MB." | |
| Session expired | "Your session has expired. Please sign in again." | |
| AI call timeout | "Analysis is taking longer than expected. Please try again." | |
