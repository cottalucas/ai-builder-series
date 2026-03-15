# ENV.md
# Environment Variables
# ─────────────────────────────────────────────────────
# Every variable the product needs, in every environment.
# Fill this alongside SPEC.md. Keep it current as you add integrations.
# Rule: if a variable is not in this file, your AI builder does not know it exists.
# Rule: never put actual values in this file — only names, descriptions, and sources.
# ─────────────────────────────────────────────────────
# Your AI builder reads this to configure the environment correctly.
# Your team reads this to onboard without asking you for variable names.
# Notion: https://www.notion.so/31d26a42061181d892f1ee9e70d57504

---

## Local setup

*Copy this block into `.env.local` in your project root (never commit this file).*
*Replace each value with your actual credentials from the sources listed below.*

```bash
# AI layer
OPENAI_API_KEY=

# Database + Auth
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

# App
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Add your own variables below
```

---

## Variable reference

*Every variable the product uses. Required = product breaks without it.*

| Variable | Required | Where used | How to get it | Local value | Prod value |
|---|---|---|---|---|---|
| `OPENAI_API_KEY` | Yes | *e.g. lib/openai.ts — AI review generation* | *e.g. platform.openai.com → API keys* | *Your dev key* | *Prod key — separate from dev* |
| `NEXT_PUBLIC_SUPABASE_URL` | Yes | *e.g. lib/supabase.ts — DB client* | *e.g. Supabase dashboard → Settings → API* | *Local Supabase URL* | *Prod Supabase URL* |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Yes | *e.g. lib/supabase.ts — client-side auth* | *e.g. Supabase dashboard → Settings → API* | *Local anon key* | *Prod anon key* |
| `SUPABASE_SERVICE_ROLE_KEY` | Yes | *e.g. API routes only — server-side DB access* | *e.g. Supabase dashboard → Settings → API* | *Local service key* | *Prod service key — never expose client-side* |
| `NEXT_PUBLIC_APP_URL` | Yes | *e.g. Auth redirects, email links* | *Your deployed URL* | *http://localhost:3000* | *e.g. https://yourdomain.com* |
| *Add more* | | | | | |

---

## Security rules for environment variables

- `NEXT_PUBLIC_` prefix = visible in the browser bundle. Only use for non-secret values.
- Service role keys, AI API keys, and any secret must NEVER have the `NEXT_PUBLIC_` prefix.
- Never commit `.env`, `.env.local`, or any file containing real values. Verify `.gitignore` covers these.
- In Vercel: set all variables in Project Settings → Environment Variables. Set separately for Preview and Production.
- Rotate keys if they are ever accidentally committed. Don't just delete the commit — the history is public.

---

## Vercel setup

*For each variable: which Vercel environments need it?*

| Variable | Development | Preview | Production |
|---|---|---|---|
| `OPENAI_API_KEY` | *e.g. Dev key* | *e.g. Dev key* | *e.g. Prod key — higher rate limit* |
| `NEXT_PUBLIC_SUPABASE_URL` | *e.g. Local project* | *e.g. Staging project* | *e.g. Prod project* |
| `SUPABASE_SERVICE_ROLE_KEY` | *e.g. Local* | *e.g. Staging* | *e.g. Prod* |
| `NEXT_PUBLIC_APP_URL` | *http://localhost:3000* | *e.g. Vercel preview URL* | *e.g. https://yourdomain.com* |
| *Add more* | | | |

---

## Onboarding checklist

*For a new developer joining the project. Every step to get the environment running.*

1. *e.g. Clone the repo*
2. *e.g. Copy `.env.example` to `.env.local` (if .env.example exists) — or create `.env.local` from the table above*
3. *e.g. Get API keys from [where they're stored — 1Password, team shared doc, etc.]*
4. *e.g. Run `supabase start` to start local Supabase*
5. *e.g. Run `supabase db reset` to apply migrations locally*
6. *e.g. Run `npm install && npm run dev`*
7. *e.g. Open http://localhost:3000 — upload flow should work end-to-end*
