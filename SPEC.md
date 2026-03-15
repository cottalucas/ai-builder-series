# SPEC.md
# Chapter 1 — Technical Specification
# Fill this AFTER the-brief.md. This is the contract between you and your AI builder.
# RULE: Never let code drift from this document. If scope changes, update this first.
# Notion: https://www.notion.so/31d26a420611810c829ce45c2324ec0b
#
# FILL ORDER:
# 1. Product summary     — what is this, who is it for
# 2. Stack               — commit to your tech choices before building
# 3. Features            — prototype scope only, nothing more
# 4. Data model          — design this before any UI work
# 5. Key flows           — numbered steps for each critical path
# 6. File structure      — agree the layout before the AI invents one
# 7. Out of scope        — explicit is better than assumed
# 8. Phase gates         — define done before you start

---

## 1. Product summary

*One paragraph. What is this, who is it for, what does it do?
Your AI builder reads this at the start of every session — make it dense and precise.*

*e.g. DeklarAI is a web app for employed residents of Kanton Zürich filing their own annual tax return (Steuererklärung). Users upload their tax documents as PDFs. The AI analyses the documents against 2024 Kanton Zürich deduction rules and produces a plain-language review showing missed or under-claimed deductions, with CHF amounts and Formular references. Prototype scope: Berufsauslagen, Homeoffice, 3a Säule, and Weiterbildung deductions only. No accounts required for prototype — session-based.*

---

## 2. Stack

*Commit to your choices before building. Vague stack = the AI invents one.*

Frontend: *e.g. Next.js 14, React 18, Tailwind CSS*
Backend: *e.g. Next.js API routes (serverless)*
Database: *e.g. Supabase — Postgres with row-level security*
Auth: *e.g. Supabase Auth — email only for prototype*
AI layer: *e.g. OpenAI GPT-4o — server-side API route only, never client-side*
File storage: *e.g. Supabase Storage — private bucket, PDF uploads*
Hosting: *e.g. Vercel*
Key libraries: *e.g. pdf-parse (text extraction), zod (schema validation), react-pdf (PDF export)*
Language: *e.g. TypeScript — strict mode, no implicit any*

---

## 3. Features (prototype scope only)

*For each feature: what it does, and what "done" looks like as an observable outcome.*
*If it's not listed here, it's out of scope. The AI builds what it reads.*

### Feature 1: *e.g. Document upload*

What it does: *e.g. User selects or drags a PDF onto the upload zone. File is validated and stored.*

Done when:
- *e.g. User can drag-drop or click-select a PDF file*
- *e.g. File type validation rejects non-PDF with message: "Please upload a PDF file."*
- *e.g. File size validation rejects files >10MB with message: "File is too large. Please upload a PDF under 10MB."*
- *e.g. Valid file uploads to Supabase Storage with a progress indicator*
- *e.g. Upload errors show inline with a retry option — no page reload required*

### Feature 2: *e.g. AI tax review*

What it does: *e.g. After upload, user triggers analysis. AI returns structured review of deductions.*

Done when:
- *e.g. "Analyse" button appears after successful upload*
- *e.g. Loading state shows: "Reviewing your documents... ~30 seconds"*
- *e.g. AI response validated against Zod schema before display*
- *e.g. Review renders as deduction cards — see data model for card fields*
- *e.g. On AI failure: "Analysis unavailable — please try again." Upload preserved. Retry button shown.*

### Feature 3: *e.g. Review display*

What it does: *e.g. Renders the AI output as readable deduction cards.*

Done when:
- *e.g. Each deduction shows: name, status badge, claimed CHF, recommended CHF, delta, reasoning, form reference*
- *e.g. Status badge colours: green = correct, amber = under-claimed, red = missed/over-claimed*
- *e.g. Summary line shows total adjustment CHF at top of review*
- *e.g. Form references render in monospace*

*Add Feature 4, 5 etc. as needed. Keep it lean — this is a prototype.*

---

## 4. Data model

*Design this before writing any UI. The AI builds UI around data structures — get this wrong and everything breaks.*

### Table: reviews
| Field | Type | Notes |
|---|---|---|
| id | uuid | Primary key, auto-generated |
| created_at | timestamp | Auto |
| status | text | pending / processing / complete / failed |
| document_url | text | Supabase Storage path |
| document_name | text | Original filename shown to user |
| output | jsonb | AI result — schema below |

### AI output schema
```json
{
  "deductions": [
    {
      "name": "string",
      "claimed_chf": 0,
      "recommended_chf": 0,
      "status": "correct | under_claimed | over_claimed | missed",
      "reasoning": "string",
      "form_reference": "string"
    }
  ],
  "summary": "string",
  "total_adjustment_chf": 0
}
```

*Replace with your actual schema. Every field the AI will produce must be defined here.*

---

## 5. Key flows

*Numbered steps. Every branch. The AI implements exactly what you write here.*

### Flow 1: *e.g. Upload and analyse (happy path)*
1. *e.g. User lands on homepage — sees upload zone immediately*
2. *e.g. User selects or drags a PDF*
3. *e.g. Client validates: type (PDF only), size (<10MB) — error shown inline if rejected*
4. *e.g. Valid file uploads to Supabase Storage — progress indicator shown*
5. *e.g. "Analyse" button appears*
6. *e.g. User clicks Analyse — loading state shown*
7. *e.g. Server extracts text, calls AI, validates output, stores result*
8. *e.g. Review renders as deduction cards*

### Flow 2: *e.g. Error recovery*
1. *e.g. AI call fails or returns invalid JSON*
2. *e.g. Review status set to "failed"*
3. *e.g. User sees: "Analysis unavailable — please try again." with Retry button*
4. *e.g. Retry reuses existing upload — user does not re-upload*
5. *e.g. If second attempt fails: "Still having trouble. Your document is saved — try again in a few minutes."*

### Flow 3: *e.g. Add your third critical flow*
1.
2.
3.

---

## 6. File structure

*Define this before the AI starts creating files. Consistency matters more than perfection.*

```
/
├── app/
│   ├── page.tsx                    # Homepage — upload zone
│   ├── review/[id]/page.tsx        # Review display
│   └── api/
│       ├── upload/route.ts         # POST — handles file upload to storage
│       └── analyse/route.ts        # POST — extracts text, calls AI, stores result
├── components/
│   ├── UploadZone.tsx
│   ├── ReviewCard.tsx
│   ├── ReviewSummary.tsx
│   └── LoadingState.tsx
├── lib/
│   ├── supabase.ts                 # Supabase client (server + client)
│   ├── openai.ts                   # AI call + response validation
│   └── prompts/
│       └── review.ts               # System prompt
├── types/
│   └── review.ts                   # TypeScript types matching AI output schema
└── *replace with your actual structure*
```

---

## 7. Out of scope

*Everything NOT listed here is IN scope by default. Be explicit.*

- *e.g. User accounts and saved review history — prototype uses anonymous sessions only*
- *e.g. Multi-canton support — Kanton Zürich only*
- *e.g. Filing integration — display only, no submission to tax authority*
- *e.g. Mobile-optimised layout — desktop first for prototype*
- *e.g. PDF export of review — add in v1.1 if prototype validates*

---

## 8. Security (prototype minimum)

*Even prototypes have users. Define the minimum security baseline now.*

- *e.g. AI API key in server-side environment variable only — never in client code*
- *e.g. Uploaded files in private Supabase Storage bucket — no public access*
- *e.g. File type and size validated server-side as well as client-side*
- *e.g. AI output validated with Zod before storage or display*
- *e.g. No PII extracted or stored beyond the document the user uploads*

---

## 9. Testing (prototype minimum)

*Define what must be tested before you call the prototype done.*

Must pass before prototype is complete:
- *e.g. Upload flow: valid PDF uploads successfully, invalid type rejected, oversized file rejected*
- *e.g. AI analysis: known test document produces expected deduction flags*
- *e.g. Error flow: simulated AI failure shows retry state, preserves upload*
- *e.g. Schema: Zod validation catches malformed AI output correctly*

Test command: `npm run test`

---

## 10. Phase gates

*Define done before you start. These are the checkpoints the AI waits for approval at.*

Phase 1 complete when:
*e.g. Upload flow works end-to-end. PDF lands in Supabase Storage. Parse status renders. Type and size rejection work.*

Phase 2 complete when:
*e.g. AI review generates and displays for a known test document. Output schema validates. Error state renders correctly.*

Prototype complete when:
*e.g. A real user uploads their own documents and receives a review that correctly identifies at least one real deduction they had not claimed — without any help from me.*
