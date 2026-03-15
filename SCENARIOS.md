# SCENARIOS.md — Edge Cases and Holdout Scenarios

> Notion reference: [Chapter 2 — The Product Brief](https://www.notion.so/31d26a420611813499bfe07c988c97ac)

This document captures the edge cases, exception paths, and holdout scenarios your product must handle. It is the safety net between your happy path and production reality.

Fill this in as you discover edge cases — from user research, QA, and live usage. Never delete a resolved scenario; mark it as resolved instead.

---

## How to use this file

- **Holdout scenarios** are cases you have deliberately chosen NOT to handle yet. They are known, named, and parked.
- **Edge cases** are cases that must be handled but are not part of the happy path.
- **Error states** are failure modes the product must communicate clearly to the user.

Your AI builder reads this file to know what to protect against and what to leave alone.

---

## Holdout scenarios

<!-- Cases that are explicitly out of scope for this version.
Name them so they don't get accidentally built or debated repeatedly. -->

| Scenario | Why it's a holdout | Revisit when |
|---|---|---|
| | | |

---

## Edge cases

<!-- Cases that must be handled, but are not the happy path.
For each: what triggers it, what should happen, and what done looks like. -->

### Edge case 1: [Name]
**Trigger:**
**Expected behaviour:**
**Status:** [ ] Open / [ ] In progress / [ ] Resolved

### Edge case 2: [Name]
**Trigger:**
**Expected behaviour:**
**Status:** [ ] Open / [ ] In progress / [ ] Resolved

---

## Error states

<!-- What can go wrong, and what does the user see when it does?
Define the error message or fallback for each failure mode. -->

| Failure mode | User-facing message | Fallback behaviour |
|---|---|---|
| AI layer returns no result | | |
| External service unavailable | | |
| Invalid user input | | |
| Authentication failure | | |
| (add more as discovered) | | |

---

## Input validation rules

<!-- What inputs does the product accept, and what are the boundaries?
Define the rules your AI builder must enforce. -->

| Input | Type | Min | Max | Notes |
|---|---|---|---|---|
| | | | | |

---

## Resolved scenarios

<!-- Move scenarios here when they're handled. Keep the record. -->

| Scenario | Resolution | Date resolved |
|---|---|---|
| | | |
