# LAUNCH.md
# Chapter 3 — Launch Strategy and GTM Plan
# ─────────────────────────────────────────────────────
# Fill this before you launch anything publicly.
# Rule: metrics instrumentation must be live BEFORE this document is executed.
# Never launch blind. No baseline = no signal.
# ─────────────────────────────────────────────────────
# FILL ORDER: Positioning → Goals → Audience → Channels → Sequence → Activation → Rollback
# Notion: https://www.notion.so/31d26a42061181eba81fd97093010d90

---

## Positioning

*One sentence. What this is, who it's for, why it matters.*
*Write this before any copy. Every channel, every message traces back to this.*

*e.g. DeklarAI reviews your Swiss tax return and tells you exactly what you've missed — in plain language, in under 2 minutes.*

Who this is for (plain language):
*e.g. Anyone in Kanton Zürich filing their own Steuererklärung.*

What problem it solves in their words:
*e.g. "I always feel like I've missed something but I don't know what."*

What we are NOT:
*e.g. Not a tax advisor. Not a filing tool. Not complicated.*

---

## Launch goals

*2–3 specific, time-bound goals. Not vanity metrics.*

| Goal | Metric | Target | By when |
|---|---|---|---|
| *e.g. First real users* | *Reviews completed* | *50* | *Week 2 post-launch* |
| *e.g. Validate willingness to pay* | *Conversion free → paid* | *>5%* | *Month 1* |
| *e.g. Organic distribution signal* | *Reviews from referral* | *>20% of total* | *Month 2* |

---

## First 100 users

Who they are:
*e.g. Swiss professionals in Zürich, 30–50, filing independently. Found on LinkedIn, expat Facebook groups, local Slack communities.*

Where they are:
- *e.g. LinkedIn — Swiss finance and tech professionals*
- *e.g. r/Switzerland and r/zurich*
- *e.g. Expat Facebook groups: Zürich Expats, English-speaking Switzerland*
- *e.g. ProductTank Zürich*

Who they trust:
*e.g. Peers who have used it. Personal posts over ads. Swiss German content for local trust.*

First 10:
*e.g. Direct outreach — find 10 people personally who fit the profile. Ask them to try it and give 5 minutes of feedback. Do this before any public launch.*

First 100:
*e.g. LinkedIn post series documenting the build and real results. 1 post/week. Each post ends with "try it free" CTA.*

---

## Channels

Channel: *e.g. LinkedIn (primary)*
Message: *e.g. "I built a tool that reviews your Swiss tax return and tells you what you've missed. 7 of the first 9 people who tried it found a deduction they hadn't claimed. Free to try."*
Format: *e.g. Short text post + one screenshot of a real (anonymised) review output*
CTA: *e.g. "Try it → [link]"*
Cadence: *e.g. 1 post/week during launch month*

Channel: *e.g. Swiss expat communities (secondary)*
Message: *e.g. "Filing your Steuererklärung? This free tool reviews it for missed deductions."*
Format: *e.g. Plain text — community rules often ban promotional images*
CTA: *e.g. Link in comment, not post body*

Channel: *e.g. Direct outreach (seed)*
Message: *e.g. Personal message to 10 specific people: "I built something useful for tax season — would you try it and give me 5 minutes of feedback?"*
Format: *e.g. 1:1 message — no template, no mass send*

---

## Launch sequence

| Timing | Action | Owner | Done? |
|---|---|---|---|
| D-14 | All acceptance criteria from PRD confirmed met | | |
| D-14 | Metrics instrumentation verified — events firing correctly | | |
| D-7 | 10 direct-outreach users complete reviews. Fix critical issues. | | |
| D-3 | Write launch post. Have 2 people review it. | | |
| D-1 | Final QA pass. Rollback criteria confirmed. | | |
| D0 | Publish. Reply to every comment within 2 hours. | | |
| D+1 | Review first-day metrics. Fix critical bugs same day. | | |
| D+7 | "Week 1 learnings" follow-up post. Metrics + what surprised you. | | |
| D+30 | Full metrics review. Decide: iterate, expand, or pivot. | | |

---

## Activation moment

*The first moment a new user experiences the core value. Everything before this is friction.*
*Design the entire onboarding as a straight line to this moment.*

The activation moment is:
*e.g. The first deduction card renders showing a CHF amount the user did not know they could claim.*

Onboarding flow to activation:
1. *e.g. Landing page — headline makes value clear immediately. No login wall.*
2. *e.g. Upload zone is the first interactive element.*
3. *e.g. Upload → Analyse → Results — 3 steps, no diversions.*
4. *e.g. Account prompt appears AFTER first review — convert on value, not on gate.*

---

## Feedback loop

How you collect it:
*e.g. Single in-app question after export: "Was this review useful?" Yes / No / Leave a note.*

Review cadence:
*e.g. Every Friday morning — read all feedback from the week. Tag by category.*

Escalation threshold:
*e.g. If >20% of reviews get "No" feedback in week 1 — pause acquisition and fix before continuing.*

---

## Rollback criteria

*Define these before launch. Not in the moment of stress.*
*If any of these are true within 48 hours: roll back or pause immediately.*

- *e.g. Error rate on review generation >10%*
- *e.g. Core flow completion rate <50% (users starting but not finishing)*
- *e.g. Any critical data security issue reported*
- *e.g. NSM declining for 3 consecutive days after launch*
