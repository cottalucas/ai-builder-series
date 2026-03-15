# VALIDATION.md
# Chapter 1 — Prototype Validation Log
# ─────────────────────────────────────────────────────
# Fill this DURING and AFTER prototype testing — not from memory weeks later.
# This is the evidence base for Chapter 2. Without it, your PRD is speculative.
# Rule: every session with a real user gets a row. No exceptions.
# ─────────────────────────────────────────────────────
# FILL ORDER: Log sessions as they happen → Write decisions immediately after each session
# WHEN TO MOVE TO CHAPTER 2: When you have 5+ real user sessions logged AND
#   at least one genuine moment of value observed AND you know what to build next.
# Notion: https://www.notion.so/31d26a42061181d892f1ee9e70d57504

---

## Exit criteria for Chapter 1

Before opening PRD.md, every box must be checked:
- [ ] At least 5 real users (not friends, not colleagues) completed the core flow without your help
- [ ] You observed at least one genuine moment of value — a user solved a real problem
- [ ] You have a revised problem statement based on what you observed (not what you assumed)
- [ ] You have a clear decision: build further, pivot the approach, or stop

---

## Session log

*Add a row for every user session. Fill it the same day — not from memory later.*

| # | Date | Who (role, not name) | Completed core flow? | Key observation | Moment of value? |
|---|---|---|---|---|---|
| *e.g. 1* | *e.g. 2026-03-10* | *e.g. Finance manager, Zürich, 41* | *Yes / No / Partially* | *e.g. Uploaded successfully but didn't know what to do with the results — no clear next action* | *Yes — said "I didn't know I could claim that" when seeing the Homeoffice card* |
| *e.g. 2* | *e.g. 2026-03-11* | *e.g. Software engineer, Zürich, 34* | *Yes* | *e.g. Immediately tried to upload a scanned PDF — failed with empty output, no error shown* | *No — left before seeing results* |
| 3 | | | | | |
| 4 | | | | | |
| 5 | | | | | |

---

## What you assumed vs. what you observed

*Fill this after session 5. This is the most important section.*
*Every row that says "Wrong" directly changes the PRD.*

| Assumption from the-brief.md | Right / Wrong / Partial | What you actually observed |
|---|---|---|
| *e.g. Users don't know deduction categories exist* | *Wrong* | *e.g. They knew the categories — they didn't know the correct amounts or form references* |
| *e.g. Privacy concern would be the biggest barrier* | *Partial* | *e.g. 3 of 5 users asked about data storage, but all proceeded after a one-line explanation* |
| *e.g. Users would use it alone at home* | *Wrong* | *e.g. Two users immediately asked if their partner could use it too* |
| *Add your own* | | |

---

## Failure modes observed

*What broke, confused users, or caused them to stop. Every item here is a fix before Chapter 2.*

| Session # | What failed | User reaction | Fix required before Chapter 2? |
|---|---|---|---|
| *e.g. 2* | *e.g. Scanned PDF returned empty output with no error message* | *e.g. Confused, thought the product was broken* | *Yes — add detection + user-facing message* |
| *e.g. 4* | *e.g. Loading state gave no time estimate — user clicked away after 20s* | *e.g. Assumed it had crashed* | *Yes — add estimated time to loading state* |
| *Add more* | | | |

---

## Revised problem statement

*Rewrite the problem statement from the-brief.md based on what you observed.*
*This becomes the "Validated problem" section in PRD.md.*

Original:
*Paste your original problem statement here*

Revised:
*e.g. Swiss Kanton Zürich residents filing independently consistently miss 2–4 deductions they are entitled to. The gap is not awareness — most know the categories exist. The gap is accuracy: they don't know the correct CHF amounts, the applicable flat rates, or the Formular references. The cost of this gap is CHF 800–1,200/year on average.*

What changed and why:
*e.g. Original assumption was unawareness. Observed reality is inaccuracy. Changes the entire product framing — from education to verification.*

---

## Decision

*One of three options. Write it clearly before moving to Chapter 2.*

Decision: Build further / Pivot the approach / Stop *(delete two)*

Rationale:
*e.g. Build further. 7 of 9 users found at least one deduction they hadn't claimed. 5 expressed genuine surprise. The core value is real. Main fix needed before Chapter 2: scanned PDF handling and loading state.*

What changes in Chapter 2 based on this:
*e.g. PRD focuses on accuracy and trust signals, not education. Design brief needs to emphasise precision aesthetic. Scanned PDF handling is a must-have, not a nice-to-have.*
