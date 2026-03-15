# user-journeys.md
# Chapter 2 — Core User Flows
# ─────────────────────────────────────────────────────
# Your AI builder reads this to understand intent before implementing any flow.
# Fill this before building features. Update it when a flow changes.
# Rule: every step must have a defined error state. No step can end in a blank screen.
# ─────────────────────────────────────────────────────
# FILL ORDER: Map your flows from entry to exit, then define failure states for each step.
# Notion: https://www.notion.so/31d26a420611813499bfe07c988c97ac

---

## How to write a journey

Each journey needs:
- Entry point: where does the user start? (URL, email, referral, direct)
- Goal: what does the user want to achieve?
- Steps: numbered path through the product — one action per step
- Exit point: what does the user have when the journey is complete?
- Failure states: what can go wrong at each step, and what does the user see?

---

## Journey 1: New user — first review

User: *e.g. First-time visitor, arrived from LinkedIn post*
Entry point: *e.g. Homepage — no account required to start*
Goal: *e.g. Get a review of their tax documents*

Steps:
1. *e.g. Lands on homepage. Sees headline and upload zone. No signup wall.*
2. *e.g. Drags PDF or clicks to select. Client validates type and size instantly.*
3. *e.g. Upload begins. Progress bar shows. "Uploading..." label visible.*
4. *e.g. Upload completes. "Ready to analyse" state. "Analyse my documents" button appears.*
5. *e.g. User clicks Analyse. Loading state: "Reviewing your documents... ~30 seconds."*
6. *e.g. Review renders. Deduction cards appear with colour-coded status.*
7. *e.g. User reads cards. Clicks "Download PDF" to save summary.*
8. *e.g. Prompted to create account to save history. Optional — not gated.*

Exit point: *e.g. User has a downloaded PDF summary of their review.*

Failure states:
- *e.g. Wrong file type → "Please upload a PDF file." Shown immediately, no upload attempted.*
- *e.g. File over 10MB → "File is too large. Please upload a PDF under 10MB."*
- *e.g. Upload fails (network) → "Upload failed — please try again." Retry without page refresh.*
- *e.g. AI returns error → "Analysis unavailable — please try again." Upload preserved, retry button shown.*
- *e.g. AI returns empty result → "No deductions flagged — everything looks correct." Never blank screen.*

---

## Journey 2: Returning user — repeat review

User: *e.g. User who ran a review last week, back with updated documents*
Entry point: *e.g. Direct URL or email — lands on dashboard*
Goal: *e.g. Run a new review with updated documents*

Steps:
1. *e.g. Lands on dashboard. Sees previous review with date and summary line.*
2. *e.g. Clicks "New review". Taken to upload flow.*
3. *e.g. Uploads new document. Triggers analysis.*
4. *e.g. New review renders. Previous review still accessible.*

Exit point: *e.g. New review complete. Both reviews in history.*

Failure states:
- *e.g. Session expired → Redirected to login. Returns to dashboard after auth. No work lost.*

---

## Journey 3: Error recovery

User: *e.g. Any user whose analysis failed*
Entry point: *e.g. Review page showing error state*
Goal: *e.g. Get their review without starting over*

Steps:
1. *e.g. User sees: "Analysis unavailable — please try again." with Retry button.*
2. *e.g. Clicks Retry. Loading state shows. Same document reused — no re-upload.*
3. *e.g. If retry succeeds: review renders normally.*
4. *e.g. If retry fails again: "Still having trouble. Your document is saved — try again in a few minutes." No third retry button.*

Exit point: *e.g. Review completed, or user reassured their document is saved.*

Failure states:
- *e.g. Persistent failure → Document preserved in storage. User not asked to re-upload.*

---

## Moments that matter

*The moments where users either commit or leave. These are the highest-leverage points.*
*Design the entire product as a straight line to moment 1.*

1. *e.g. First deduction card renders with a specific CHF amount the user didn't know about — this is the activation moment. Everything before this is friction.*
2. *e.g. "Download PDF" click — signals intent to use the output. Strong retention predictor.*
3. *e.g. Account creation prompt — shown after first review, not before. Convert on value, not on gate.*
