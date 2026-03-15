# implementation-plan.md
# Chapter 3 — Phased Rollout and Growth Plan
# ─────────────────────────────────────────────────────
# Fill this when you are ready to grow. Not before.
# This document defines how the product gets better over time without proportional effort.
# ─────────────────────────────────────────────────────
# Notion: https://www.notion.so/31d26a42061181eba81fd97093010d90

---

## Growth engine

*How this product grows. The fundamental mechanism.*
*Is it word of mouth? SEO? Virality? Community? Paid acquisition?*
*Describe it in 2–3 sentences before anything else.*

*e.g. DeklarAI grows through seasonal word-of-mouth. Tax season creates a concentrated burst of high-intent users who share results with their partner, flatmates, or colleagues. One satisfied user in a household typically refers 1–2 others within the same filing season.*

---

## Phase 1: Traction

Goal: *e.g. 50 real reviews completed. At least one user pays. Know whether to continue.*
Time horizon: *e.g. Month 1–2*

What we do:
- *e.g. Direct outreach to 10 target users before any public launch*
- *e.g. LinkedIn post series — 1 post/week documenting build and real results*
- *e.g. Interview every user who completes a review — one question: "What would you have done without this?"*
- *e.g. Run the product ourselves — use it personally, find every rough edge*

Phase 1 complete when:
*e.g. 50 completed reviews. Correction rate <30%. At least 5 users express willingness to pay.*

---

## Phase 2: Retention

Goal: *e.g. Users come back next tax season. Day-30 retention >20% on early cohort.*
Time horizon: *e.g. Month 3–6*

What we do:
- *e.g. Build saved review history — give users a reason to return*
- *e.g. Annual reminder email: "Tax season is coming — your last review found CHF X in missed deductions"*
- *e.g. Run cohort analysis: are Month 2 users retaining better than Month 1?*
- *e.g. Weekly error analysis cycle — every AI failure category becomes a test*

Phase 2 complete when:
*e.g. Day-30 retention >20%. Month 2 cohort retains better than Month 1. AI error rate <5%.*

---

## Phase 3: Compounding

Goal: *e.g. Product grows without proportional acquisition spend. Word of mouth >40% of new reviews.*
Time horizon: *e.g. Month 7+*

What we do:
- *e.g. Referral mechanic — shareable review card drives organic awareness*
- *e.g. Partner return support — doubles the addressable household*
- *e.g. Building in public — weekly post, documented proof, not polished content*
- *e.g. Expand to Kanton Bern and Basel-Stadt — same codebase, new rule sets*

Phase 3 complete when:
*e.g. MoM growth >15% with <20% from paid/direct acquisition.*

---

## Growth loops

*A loop: action → output → input back into the same loop. Define the ones that compound.*

Loop 1: *e.g. Word-of-mouth*
```
User completes review → finds missed deduction → tells partner/colleague → new user tries it
```
What makes it compound: *e.g. Tax season creates natural social context — people talk about taxes.*
What breaks it: *e.g. If AI output is wrong, the first referral conversation kills trust immediately.*

Loop 2: *e.g. Data flywheel*
```
More reviews → more traces → error analysis → better system prompt → better output → more trust → more reviews
```
What makes it compound: *e.g. Each eval cycle raises the floor. Product improves with volume.*
What breaks it: *e.g. Skipping the error analysis cycle. Data collects but nothing improves.*

Loop 3: *e.g. Building in public*
```
Ship something → document it publicly → new users discover it → more reviews → more to document
```
What makes it compound: *e.g. Posts have a long tail — found during tax season months after written.*
What breaks it: *e.g. Stopping. The loop only runs if you ship consistently.*

---

## Metrics

NSM: *e.g. Reviews completed where at least one deduction was flagged and user exported the summary*

| Event | What it measures | Target |
|---|---|---|
| Review started | Acquisition intent | *Baseline for funnel* |
| Review completed | Activation | *>60% of started* |
| Deduction flagged | Core value delivered | *>80% of completed* |
| Export clicked | Committed value | *>40% of completed* |
| Return (30 days) | Retention signal | *>20% of Month 1 users* |
| Referral attributed | Loop 1 running | *>20% of new users* |

Analytics tool: *e.g. PostHog*
Review cadence: *e.g. Every Friday — 15 minutes, same dashboard, same questions*

---

## Error analysis cycle

*For AI-powered products. The highest-ROI post-launch activity.*
*Without this cycle, AI products plateau. The model does not improve itself.*

Weekly (15 minutes):
1. *e.g. Pull 10 random review traces from the past week*
2. *e.g. Label each: success / failure / partial / unclear*
3. *e.g. If a failure doesn't fit existing categories — create a new one*
4. *e.g. If any category has 3+ examples — write a test case, add to eval suite*

Monthly (1 hour):
1. *e.g. Run full eval suite against current system prompt*
2. *e.g. Review failure category distribution — is anything growing?*
3. *e.g. Update system prompt based on most common failure patterns*
4. *e.g. Document changes in PROGRESS.md — what changed, why, what evals showed*

Triggers a full retrospective:
- *e.g. Error rate spikes above 10%*
- *e.g. New failure category appears in >5 traces in one week*
- *e.g. User reports factually incorrect advice*
