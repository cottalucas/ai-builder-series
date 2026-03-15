# Stack

## Framework and tools

Language: *e.g. TypeScript — strict mode, no implicit any*
Frontend: *e.g. Next.js 14 App Router, React 18, Tailwind CSS*
Backend: *e.g. Next.js API routes (serverless)*
Database: *e.g. Supabase — Postgres with row-level security enabled on all tables*
Auth: *e.g. Supabase Auth — email + Google OAuth, JWT in httpOnly cookie*
AI layer: *e.g. OpenAI GPT-4o — server-side only, NEVER in client code*
Storage: *e.g. Supabase Storage — private bucket, signed URLs only*
Hosting: *e.g. Vercel*

## Commands

- `npm run dev` — start local dev server
- `npm run build` — production build
- `npm run typecheck` — TypeScript check (run before every commit)
- `npm run lint` — linter (run before every commit)
- `npm run test` — full test suite
- `npm run test:unit` — unit tests only (faster)
- *Add your own commands here as you discover them*

## Codebase layout

Entry point: *e.g. app/page.tsx*
UI components: *e.g. components/ — never auto-generate files here*
Business logic: *e.g. lib/ — AI calls, data access, validation*
API routes: *e.g. app/api/*
Types: *e.g. types/ — all TypeScript types, no inline type definitions in components*
Prompts: *e.g. lib/prompts/ — all AI system prompts*
Migrations: *e.g. supabase/migrations/ — never edit existing migrations*

Never touch (auto-generated or locked):
- *e.g. components/ui/ — auto-generated design system*
- *e.g. .next/ — build output*
- *e.g. supabase/migrations/ — only add new migrations, never edit existing*

## Conventions

Naming: *e.g. camelCase for variables and functions, PascalCase for components, kebab-case for files*
Imports: *e.g. ES modules only. Destructure where possible: `import { foo } from 'bar'`*
Error handling: *e.g. Always try/catch on async. Log error + context. Never surface raw errors to users.*
AI output: *e.g. Always validate AI responses with Zod before use. Reject and log if schema fails.*
Secrets: *e.g. All secrets in .env — never hardcoded, never NEXT_PUBLIC_ prefixed*
