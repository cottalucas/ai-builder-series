# ARCHITECTURE.md
# Chapter 2 — Technical Architecture
# Fill this when moving from prototype to product.
# Your AI builder reads this when making ANY structural decision.
# If the architecture changes, update this file FIRST. Code must match this document.
# Notion: https://www.notion.so/31d26a420611813499bfe07c988c97ac

---

## System overview

*Draw the full system as a flow. Every component and connection. Replace the example completely.*

```
Example — DeklarAI:

User browser
  → Next.js frontend (Vercel)
      → /api/upload      → Supabase Storage (PDF files, private bucket)
      → /api/analyse     → OpenAI API (server-side only)
                         → Supabase DB (stores review result as JSONB)
      → /review/[id]     ← reads from Supabase DB

Auth: Supabase Auth — JWT in httpOnly cookie
Storage: Supabase Storage — private bucket, signed URLs only
All AI calls: server-side only — API key never exposed to client
```

*Replace above with your actual system diagram.*

---

## Components

### Frontend

Framework: *e.g. Next.js 14 App Router, React 18, Tailwind CSS*
Hosted on: *e.g. Vercel — auto-deploys from main branch on push*
Responsibilities: *e.g. Upload UI, review display, auth flow, PDF export*
State management: *e.g. React useState only — no external state library for prototype*
Notes: *e.g. Mobile-responsive at 640px breakpoint. No SSR for authenticated pages.*

### Backend / API

Framework: *e.g. Next.js API routes (serverless functions)*
Hosted on: *e.g. Vercel serverless — 60s max execution timeout*
Responsibilities: *e.g. File upload handling, AI orchestration, result storage*
Critical limits: *e.g. 60s function timeout. Large PDFs + slow AI responses may exceed this. Plan: background jobs at scale.*
Notes: *e.g. All routes require authentication except /api/health*

### Database

Technology: *e.g. Supabase — Postgres 15 with pgvector extension*
Hosted on: *e.g. Supabase cloud — eu-central-1 region (Swiss data residency)*
Schema file: *e.g. supabase/migrations/001_initial.sql*
Row-level security: *e.g. Enabled on all tables. Users can only read/write their own records.*
Backup policy: *e.g. Supabase daily backups — 7-day retention on free tier*

### AI layer

Model: *e.g. GPT-4o via OpenAI API*
Called from: *e.g. /api/analyse only — never from any client-side code*
Prompt location: *e.g. src/lib/prompts/system.ts*
Output validation: *e.g. Zod schema in types/review.ts — all AI responses validated before storage*
Context limit: *e.g. Input truncated at 12,000 tokens. User notified if document is truncated.*
Fallback: *e.g. On API error or invalid JSON response: status → "failed", user sees retry option*
Cost control: *e.g. Rate limit: 10 analyses per user per day on free tier*

### Auth

Provider: *e.g. Supabase Auth*
Methods: *e.g. Email + password, Google OAuth*
Session: *e.g. JWT in httpOnly cookie — 7-day expiry, auto-refresh*
Protected routes: *e.g. All /dashboard/* and /review/* routes require active session*

### Storage

Provider: *e.g. Supabase Storage*
Bucket: *e.g. "documents" — private, no public access*
Access: *e.g. Signed URLs — 1-hour expiry. Generated server-side only.*
Retention: *e.g. Files deleted after 30 days or immediately on account deletion*
Limits: *e.g. 10MB per file, PDF only, 1GB total on free tier*

### External integrations

*List every third-party service. Anything not listed here should not be in the codebase.*

| Service | Purpose | Critical path | Fallback |
|---|---|---|---|
| *e.g. OpenAI* | *AI analysis* | *Yes* | *Show error, preserve upload* |
| *e.g. Supabase* | *DB + Auth + Storage* | *Yes* | *503 page* |
| *e.g. Vercel* | *Hosting + CDN* | *Yes* | *N/A* |
| *Add more* | | | |

---

## Data flow — core case

*The exact path data takes for the primary user action. Step by step.*

1. *e.g. User selects PDF → client validates type (PDF only) and size (<10MB) before any upload*
2. *e.g. POST /api/upload → file streamed to Supabase Storage private bucket → review record created with status "pending"*
3. *e.g. User clicks Analyse → POST /api/analyse → file retrieved from storage → text extracted via pdf-parse*
4. *e.g. Extracted text + system prompt → GPT-4o → JSON response*
5. *e.g. JSON validated against Zod schema → stored in reviews.output (JSONB) → status updated to "complete"*
6. *e.g. Frontend polls /api/review/[id] every 3s → on "complete", renders review cards from output JSON*
7. *e.g. On any failure: status → "failed" → user sees retry option → document preserved*

---

## Data model

*Every table. Every field that matters. If it's in the database, it's in this section.*

### Table: users *(managed by Supabase Auth)*
| Field | Type | Notes |
|---|---|---|
| id | uuid | Primary key |
| email | text | Unique |
| created_at | timestamp | Auto |

### Table: reviews
| Field | Type | Notes |
|---|---|---|
| id | uuid | Primary key |
| user_id | uuid | FK → auth.users — RLS on this field |
| created_at | timestamp | Auto |
| status | text | pending / processing / complete / failed |
| document_url | text | Supabase Storage path |
| document_name | text | Original filename |
| output | jsonb | AI review result — schema below |
| error_message | text | Populated on failure, null on success |

### AI output schema
```json
{
  "deductions": [
    {
      "name": "string — deduction category name",
      "claimed_chf": "number — amount user claimed",
      "recommended_chf": "number — correct amount per rules",
      "status": "correct | under_claimed | over_claimed | missed",
      "reasoning": "string — plain language explanation",
      "form_reference": "string — e.g. Formular 5, Ziffer 5.1"
    }
  ],
  "summary": "string — one sentence summary",
  "total_adjustment_chf": "number — net delta"
}
```

*Replace with your actual schema.*

---

## Infrastructure

Environments:
- local: *e.g. Next.js dev server + Supabase local (Docker)*
- staging: *e.g. Vercel preview deployments + Supabase staging project*
- production: *e.g. Vercel prod + Supabase prod*

CI/CD: *e.g. GitHub Actions — typecheck + lint on every PR. Vercel auto-deploys main to production on merge.*
Secrets: *e.g. All API keys in Vercel environment variables. .env.local for local dev. Never committed.*
Monitoring: *e.g. Vercel Analytics (Web Vitals). Supabase dashboard (DB metrics). No custom APM yet.*
Alerting: *e.g. None yet — manual monitoring. Add Sentry before launch.*

---

## Security

*Every security decision. If it's not written here, it doesn't exist.*

- *e.g. API keys: server-side only — NEXT_PUBLIC_ prefix never used for secrets*
- *e.g. File access: signed URLs only — no public bucket access*
- *e.g. Auth: httpOnly cookies — no localStorage for tokens*
- *e.g. RLS: enabled on all Supabase tables — users cannot access other users' data*
- *e.g. Input validation: file type and size validated client-side AND server-side*
- *e.g. AI output: validated with Zod before storage — malformed JSON rejected*
- *e.g. Rate limiting: 10 analyses/user/day — prevents API cost abuse*
- *e.g. CORS: restricted to production domain — no wildcard origins*
- *e.g. Data residency: EU region only — Supabase eu-central-1*

---

## Testing

*What is tested, how, and what the coverage targets are.*

Unit tests:
- *e.g. AI output schema validation (Zod) — all valid and invalid JSON variations*
- *e.g. File validation logic — type rejection, size rejection, edge cases*
- *e.g. PDF text extraction — known documents with expected output*

Integration tests:
- *e.g. Upload flow end-to-end — file lands in storage, review record created*
- *e.g. Analyse flow end-to-end — mock AI response, output stored correctly*

E2E tests:
- *e.g. Full user journey: upload → analyse → view review → export PDF*
- *e.g. Error recovery: failed analysis → retry → success*

Test framework: *e.g. Vitest for unit/integration, Playwright for E2E*
Coverage target: *e.g. 80% on lib/ and api/ routes. UI components not prioritised.*
Run command: `npm run test`

---

## What breaks first at 10x

*Name the bottleneck before you hit it. One fix per item.*

| Bottleneck | Breaks at | Fix |
|---|---|---|
| *e.g. OpenAI rate limits* | *~50 concurrent users* | *Add request queue (Upstash Redis)* |
| *e.g. Vercel function timeout (60s)* | *Large multi-page PDFs* | *Move analysis to background job* |
| *e.g. Supabase free tier storage (1GB)* | *~2,000 documents* | *Add cleanup job at 80% capacity* |
| *e.g. No retry logic on AI calls* | *Any transient API error* | *Add exponential backoff before launch* |

---

## Technical debt

*Shortcuts taken that need addressing. Honest and current.*

| Item | Why it's debt | Priority | Fix by |
|---|---|---|---|
| *e.g. No retry on AI calls* | *Transient failures → user error* | *High* | *Before launch* |
| *e.g. PDF extraction is best-effort* | *Scanned docs return garbled text* | *Medium* | *v1.1* |
| *e.g. No rate limiting on API routes* | *Single user can spam AI calls* | *High* | *Before launch* |
| *e.g. No error monitoring (Sentry)* | *Production failures invisible* | *High* | *Before launch* |
