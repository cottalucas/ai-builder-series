# design-brief.md
# Chapter 2 — Visual and UX Direction
# ─────────────────────────────────────────────────────
# The minimum context your AI builder needs to make consistent design decisions.
# Without this file, your AI builder invents a visual language every session.
# Fill this once. Update when the design direction changes.
# ─────────────────────────────────────────────────────
# FILL ORDER: Direction → Brand → Colours → Typography → Components → Layout
# Notion: https://www.notion.so/31d26a420611813499bfe07c988c97ac

---

## Design direction

*2–3 sentences describing the feeling. Your AI builder uses this to make judgment calls.*
*e.g. DeklarAI feels like a trusted Swiss professional — precise, clean, and understated. Not flashy. Not corporate. The kind of tool you trust with sensitive documents because it looks like it was built by someone who takes accuracy seriously.*

We are NOT:
*What this product deliberately avoids. Be specific.*
*e.g. Not colourful or playful. Not generic SaaS blue. Not a dashboard with gradients.*

Reference products:
*2–3 products whose design you want your AI builder to reference for judgment calls.*
*e.g. Linear (precision, speed), Stripe (trust signals, data clarity), Swiss government forms (austere, functional)*

---

## Brand

Product name: *e.g. DeklarAI*
Tagline: *e.g. Your tax return, reviewed.*
Voice: *e.g. Direct and precise. Plain language. Never hedges. States what it found and why.*

Tone by context:
- Loading/analysis: *e.g. Calm — "Reviewing your documents..."*
- Results: *e.g. Specific — "2 deductions flagged. Estimated adjustment: CHF 840."*
- Errors: *e.g. Honest — "Analysis unavailable — please try again."*
- Empty states: *e.g. Reassuring — "Everything looks correct. No missed deductions found."*

---

## Colours

*Replace hex values with your actual palette. Every role must be defined.*

| Role | Hex | Where used |
|---|---|---|
| Background | *e.g. #F8F7F4* | *Page background — warm off-white, not pure white* |
| Surface | *e.g. #FFFFFF* | *Cards, modals, inputs* |
| Primary | *e.g. #1A1A1A* | *Primary buttons, headings, key text* |
| Secondary text | *e.g. #6B6B6B* | *Labels, captions, supporting copy* |
| Border | *e.g. #E5E4E0* | *Card borders, dividers, input outlines* |
| Success | *e.g. #2D6A4F* | *Correctly claimed deductions* |
| Warning | *e.g. #B5630A* | *Under-claimed deductions* |
| Error | *e.g. #C0392B* | *Missed deductions, system errors* |

---

## Typography

*Define every text role. Your AI builder applies these without asking.*

| Role | Font | Size | Weight | Notes |
|---|---|---|---|---|
| Heading 1 | *e.g. Inter* | *e.g. 28px* | *e.g. 600* | *Page titles only* |
| Heading 2 | *e.g. Inter* | *e.g. 20px* | *e.g. 600* | *Section and card headings* |
| Body | *e.g. Inter* | *e.g. 16px* | *e.g. 400* | *All paragraph text* |
| Label | *e.g. Inter* | *e.g. 13px* | *e.g. 500* | *Input labels, captions, badges* |
| Amount | *e.g. Inter* | *e.g. 20px* | *e.g. 600* | *CHF figures — always prominent* |
| Code/reference | *e.g. JetBrains Mono* | *e.g. 13px* | *e.g. 400* | *Form references e.g. Formular 5, Ziffer 5.1* |

Line height: *e.g. 1.6 for body, 1.2 for headings*

---

## Spacing

Base unit: *e.g. 4px*
Scale: *e.g. 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64px*
Card padding: *e.g. 24px*
Input padding: *e.g. 12px vertical, 16px horizontal*
Page margin: *e.g. 24px mobile, 48px desktop*

---

## Components

*Define once. Your AI builder uses these patterns without asking.*

Buttons:
- *e.g. Primary: #1A1A1A fill, white text, 6px radius, 44px min height*
- *e.g. Secondary: 1px #1A1A1A border, transparent fill*
- *e.g. Destructive: #C0392B fill*
- *e.g. Disabled: 40% opacity, not-allowed cursor*

Forms:
- *e.g. Labels always above inputs — never placeholder-only*
- *e.g. Validation inline below the field in #C0392B at 13px*
- *e.g. Focus: 2px ring in primary colour*
- *e.g. Error fields: border turns #C0392B*

Cards:
- *e.g. 1px #E5E4E0 border, 8px radius, 24px padding, no shadow*
- *e.g. Status badge top-right: pill shape, 999px radius, 12px text*

Loading states:
- *e.g. Short (<2s): spinner only, centred*
- *e.g. Long (AI analysis): message + estimated time. e.g. "Reviewing your documents... ~30 seconds"*
- *e.g. No skeleton screens — content appears complete or not at all*

Empty states:
- *e.g. Short message + single action. No illustrations. e.g. "No reviews yet." + upload button*

Error states:
- *e.g. Inline errors below the relevant element*
- *e.g. System errors as toast, bottom-right, 5s auto-dismiss*
- *e.g. Never show raw error codes or stack traces to users*

---

## Layout

Max content width: *e.g. 720px — single column, always centred*
Responsive: *e.g. Desktop-first. Mobile breakpoint at 640px — same layout, full-width.*
Navigation: *e.g. Minimal top bar. Logo left, account right. No sidebar.*
Border radius: *e.g. Inputs and buttons: 6px. Cards: 8px. Modals: 12px.*
Shadows: *e.g. Cards: 0 1px 3px rgba(0,0,0,0.06). No dramatic shadows.*
