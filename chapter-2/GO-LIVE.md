# GO-LIVE.md
# Chapter 2 — Pre-Production Checklist
# ─────────────────────────────────────────────────────
# The checklist between "it works on my machine" and "it works for a stranger."
# Run this with your AI builder before every production deployment.
# Rule: every unchecked box is a known risk you are choosing to accept.
# Rule: do not call the product "live" until this checklist is complete.
# ─────────────────────────────────────────────────────
# Notion: https://www.notion.so/31d26a420611813499bfe07c988c97ac

---

## How to use this checklist

Work through it top to bottom with your AI builder.
For each item: either confirm it's done, fix it, or explicitly decide to accept the risk and note why.
Never skip an item silently.

---

## 1. Environment and configuration

- [ ] All environment variables in ENV.md are set in the production environment
- [ ] `NEXT_PUBLIC_APP_URL` points to the live production domain (not localhost)
- [ ] No `.env` or `.env.local` files committed to the repo — verify with `git log --all -- .env`
- [ ] AI API key is server-side only — verify it does not appear in `npm run build` output
- [ ] Supabase project is the production project, not the local or staging project
- [ ] Supabase anon key and service role key are the production keys

---

## 2. Database

- [ ] All migrations have been applied to production — run `supabase db status` to verify
- [ ] Row-level security is enabled on all tables that store user data
- [ ] Tested: User A cannot read User B's rows (run scenario S007 from SCENARIOS.md)
- [ ] Storage bucket is set to private (not public)
- [ ] Signed URL expiry is set correctly (not permanent)
- [ ] Retention/cleanup job is configured if you committed to file deletion on a schedule

---

## 3. Auth

- [ ] Sign-up flow works in production (not just locally)
- [ ] Email confirmation works — test with a real email address
- [ ] Password reset works end-to-end in production
- [ ] Session persists after page refresh in production
- [ ] Redirect URLs in Supabase Auth settings point to the production domain

---

## 4. Core flow — manual test in production

*Test the exact happy path in the production environment, not locally.*

- [ ] Upload a real PDF in production — file lands in Supabase Storage
- [ ] Analysis completes in production — AI call succeeds, result stored in DB
- [ ] Review renders correctly in production
- [ ] Export PDF works in production
- [ ] Error state renders correctly — test by uploading an invalid file type

---

## 5. Error handling

- [ ] No raw error messages visible to users — test every error state from SCENARIOS.md
- [ ] 404 page exists and is not the default framework 404
- [ ] 500/error page exists and includes a way to contact support or retry
- [ ] Failed AI call shows the correct fallback message, not a blank screen
- [ ] Upload failure shows the correct message, file picker resets correctly

---

## 6. Performance

- [ ] `npm run build` completes without errors or warnings
- [ ] `npm run typecheck` passes with zero errors
- [ ] `npm run lint` passes with zero errors
- [ ] Core flow completes in under 60 seconds on a normal connection (AI analysis included)
- [ ] No console errors on the homepage, upload flow, or review display in production

---

## 7. Security

- [ ] No API keys visible in page source or browser network tab
- [ ] HTTPS is active — domain redirects HTTP to HTTPS
- [ ] File upload rejects non-PDF files server-side (not just client-side)
- [ ] File upload rejects oversized files server-side (not just client-side)
- [ ] No sensitive data logged to the console in production

---

## 8. Monitoring

- [ ] Error monitoring is active — you will be notified of production errors
- [ ] Analytics events are firing — verify the activation event triggers on a test run
- [ ] You know how to check server logs if something breaks at 2am

---

## 9. Rollback plan

- [ ] You know the exact command or button to roll back to the previous deploy
- [ ] The previous working deploy is identifiable in your deploy history
- [ ] Rollback criteria from LAUNCH.md are defined and agreed

---

## 10. Final confirmation

- [ ] You have personally completed the core flow end-to-end in the production environment
- [ ] At least one other person has tested it in production (not just locally)
- [ ] All items above are checked, or risks are explicitly accepted with a written note below

Accepted risks:
*List any unchecked items you are knowingly shipping with, and why.*
*e.g. Item 8 — no error monitoring yet. Accepted: this is a 10-user beta. Will add before public launch.*

Sign-off: *Your name + date*
