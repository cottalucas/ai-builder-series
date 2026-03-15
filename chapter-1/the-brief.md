# the-brief.md
# Chapter 1 — The Prototype Brief
# Fill this BEFORE writing any code. This is the most important document in Chapter 1.
# Your AI builder uses this as its primary context for everything it builds.
# Notion: https://www.notion.so/31d26a42061181d892f1ee9e70d57504
#
# FILL ORDER (takes 1–2 hours first time, 30 min after that):
# 1. The problem   — be specific, name the friction point and when it happens
# 2. The user      — one real person, not a segment
# 3. The solution  — what it does AND what it does not do
# 4. Scope         — must-have / nice-to-have / out of scope
# 5. Constraints   — stack, time, regulatory, language, budget
# 6. Success signal — a behaviour, not a metric
# 7. Open questions — assumptions that could be wrong

---

## 1. The problem

Problem statement:
*Describe the specific friction point. Avoid "people waste time on X." Name the exact moment the problem occurs and why it matters.*
*e.g. Swiss residents in Kanton Zürich filing their own tax returns consistently miss 2–4 deductions they are legally entitled to — not because they are negligent, but because the rules are complex, jurisdiction-specific, and buried in 40-page PDFs. The gap between what they claim and what they could claim is typically CHF 500–2,000 per year.*

Who experiences it:
*One sentence. Role, context, geography.*
*e.g. Employed professionals in Kanton Zürich, age 30–55, filing their Steuererklärung independently.*

When it happens:
*The specific moment. Not "when filing taxes" — the exact trigger.*
*e.g. Every January–March when they sit down to file and realise they don't know what deductions apply to their situation — and the deadline is two weeks away.*

What they do today:
*Their actual current workaround. This is your competition.*
*e.g. Either guess and under-claim, pay CHF 200–400 for a tax advisor for a 45-minute job, or ask a colleague who may also be guessing.*

---

## 2. The user

Primary user:
*One specific person — not a segment. Give them a name, role, context, level of sophistication.*
*e.g. Sandra, 36, product manager at a Zürich tech company. Files her own taxes. Comfortable with digital tools. Not a finance expert. Has a Lohnausweis, contributes to 3a, works from home two days a week. Speaks German and English. Trusts technology but needs to feel the output is accurate.*

What they care about most:
*e.g. Not leaving money on the table. Knowing she hasn't missed anything obvious. Getting it done in under an hour.*

What they are afraid of:
*e.g. Getting it wrong and being audited. Trusting an AI that gives her wrong numbers. Uploading sensitive documents to an unknown tool.*

---

## 3. The solution

What it does:
*2–3 sentences. Specific. What the user experiences.*
*e.g. User uploads their tax documents as PDFs. The product analyses them against Kanton Zürich 2024 deduction rules and produces a plain-language review showing: which deductions they claimed correctly, which they under-claimed, and which they missed entirely — with CHF amounts and the exact Formular reference for each.*

What it does NOT do:
*Explicit exclusions. Anything not excluded here is in scope by default.*
*e.g. Does not file the return. Does not provide legal tax advice (includes disclaimer on every output). Does not support cantons other than Zürich. Does not work for self-employed.*

---

## 4. Prototype scope

Must have — the prototype fails without these:
- *e.g. PDF upload*
- *e.g. AI analysis producing at least 3 deduction categories*
- *e.g. Output showing: deduction name, claimed CHF, recommended CHF, reasoning, form reference*

Nice to have — only if must-haves are complete:
- *e.g. Export review as PDF*
- *e.g. Side-by-side comparison view*

Out of scope — do not build, do not discuss:
- *e.g. User accounts and history*
- *e.g. Multi-canton support*
- *e.g. Filing integration*
- *e.g. Payment / monetisation*

---

## 5. Constraints

Technical:
*e.g. Must run on Vercel free tier. All AI calls server-side. No proprietary infrastructure.*

Time:
*e.g. Working prototype in 2 weeks of evenings and weekends.*

Regulatory / legal:
*e.g. Must not present output as legal advice — disclaimer required on every review. Swiss data residency preferred (EU servers minimum).*

Language / geography:
*e.g. Interface in German and English. Tax rules are Kanton Zürich 2024 only.*

Budget:
*e.g. Under CHF 50/month in API costs at prototype scale (<100 users).*

---

## 6. Success signal

The prototype succeeds when:
*A behaviour, not a metric. The exact thing a real user does or says that proves this is worth continuing.*
*e.g. A real user — not a friend, not a colleague — uploads their own tax documents, reads the review, and says "I didn't know I could claim that." Without me explaining anything. Without them asking for clarification. If this happens once, the prototype worked.*

---

## 7. Open questions

*The assumptions you're making that could be wrong. These are what the prototype will test.*

- *e.g. Will users trust an AI with their tax documents? (Data privacy may kill this before we start)*
- *e.g. Is the AI output accurate enough to be useful, or will errors destroy trust immediately?*
- *e.g. Is the problem real enough that people would pay for this — or do most people already use advisors and this market is smaller than assumed?*
- *e.g. Can we extract enough signal from a PDF tax document without OCR on scanned docs?*
