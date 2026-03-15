# PRD.md
# Chapter 2 — Product Requirements Document
# ─────────────────────────────────────────────────────
# Fill this AFTER your prototype has been validated by real users.
# Every field should be backed by something you observed — not assumed.
# Rule: if you can't point to evidence, you're not ready for Chapter 2.
# ─────────────────────────────────────────────────────
# FILL ORDER: Vision → Validated problem → User → Jobs to be done → Features → Metrics
# Notion: https://www.notion.so/31d26a420611813499bfe07c988c97ac

---

## Product vision

*2–3 sentences. Where does this go if everything works?*
*Specific enough to reject roadmap items that don't serve it.*
*Not a tagline — a direction.*

*e.g. DeklarAI becomes the default first step for Swiss residents filing their own taxes — the layer between raw documents and a completed return that makes everyone feel like they have a tax expert in their pocket. Long-term: covers all cantons, integrates with filing software, and builds a data moat from anonymised deduction patterns that no competitor can replicate.*

---

## Validated problem

Problem:
*Rewrite from the-brief.md, sharpened by what you observed in the prototype.*
*e.g. Swiss Kanton Zürich residents filing independently consistently miss 2–4 deductions. Most common: Homeoffice (wrong rate), 3a Säule (not claimed), Weiterbildung (wrong category).*

Evidence from prototype:
*What did users actually say or do? Specific observations only.*
*e.g. 7 of 9 prototype users had at least one under-claimed deduction identified. 5 said "I didn't know I could claim that." 2 asked if it works for their partner's return.*

What changed from the brief:
*What assumption turned out to be wrong?*
*e.g. Original assumption: users don't know deduction categories exist. Reality: they know the categories but don't know the correct amounts or form references. The gap is accuracy, not awareness.*

---

## Target user

Primary user:
*Updated from prototype learnings — sharper than your original brief.*
*e.g. Employed professional in Kanton Zürich, 30–50. High trust in digital tools. Will share documents if privacy is clearly addressed upfront. Prefers German UI but comfortable with English.*

Secondary user:
*Who else showed up unexpectedly?*
*e.g. Partners and spouses of primary users — second most common use case observed.*

Not building for:
*Explicit exclusions prevent scope creep and misaligned roadmap decisions.*
*e.g. Self-employed, freelancers, users outside Kanton Zürich — different rules, out of scope until product is stable.*

---

## Jobs to be done

*What is the user hiring this product to do?*
*Format: When [situation], I want to [motivation], so I can [outcome].*

Primary job:
*e.g. When I sit down to file my tax return, I want to know if I've missed anything, so I can claim everything I'm entitled to without paying for an advisor.*

Secondary job:
*e.g. When I'm done filing, I want a record of what was reviewed, so I can refer back to it if questioned.*

---

## Features

Now — committed for this release:

| Feature | What it does | Done when |
|---|---|---|
| *e.g. Multi-document upload* | *Accept Lohnausweis + additional docs in one session* | *User can upload up to 5 files. All included in analysis. Each shows individual parse status.* |
| *e.g. Deduction comparison* | *Show claimed vs recommended side by side with delta* | *Each card shows: claimed CHF, recommended CHF, delta, reasoning, Formular reference.* |
| *e.g. Review export* | *User saves review as PDF* | *"Download PDF" generates clean summary. Filename: product-review-YYYY-MM-DD.pdf* |

Next — planned, not committed:

| Feature | Why it's next |
|---|---|
| *e.g. Saved review history* | *Prototype users asked to access last year's review. Required for retention.* |
| *e.g. Partner return support* | *Second most requested in prototype. Same codebase, separate session.* |

Later — on the radar:
- *e.g. Multi-canton support*
- *e.g. Year-over-year comparison*
- *e.g. Filing software integration*

Never — explicitly not building:
- *e.g. Tax advice or legal opinions — liability, out of scope permanently*
- *e.g. Direct filing submission — regulatory complexity, not our wedge*

---

## North Star Metric

*The one number that, when it goes up, you are confident the product is delivering real value.*
*Not a revenue metric. A user behaviour metric.*

NSM: *e.g. Reviews completed where at least one deduction was flagged and the user exported the summary*
Baseline: *e.g. 0 (pre-launch)*
Target at 3 months: *e.g. 200 completed reviews/month*

Guardrail metrics — must not get worse while optimising for NSM:
- *e.g. Error rate on review generation — must stay below 5%*
- *e.g. Support tickets per 100 reviews — must stay below 3*
- *e.g. p95 response time — must stay below 45 seconds*

---

## Constraints

*Hard limits the product must operate within. Non-negotiable.*

- *e.g. Swiss data residency — user documents must not leave EU/CH infrastructure*
- *e.g. No legal advice framing — every output must include: "This is an analysis tool, not legal tax advice."*
- *e.g. Kanton Zürich rules only until v2 — do not generalise logic to other cantons*
- *e.g. GDPR compliance — explicit consent for document processing, right to deletion*

---

## Open questions

*Assumptions still to be tested before committing the roadmap.*

- *e.g. Will users pay? What price point? We have usefulness signal but not willingness-to-pay.*
- *e.g. How accurate is AI on edge cases? Tested 9 users — need 50+ before making accuracy claims.*
- *e.g. Does addressing privacy concerns upfront increase or decrease conversion?*
