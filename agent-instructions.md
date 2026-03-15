# agent-instructions.md

> Notion reference: [Chapter 1 — The Prototype Brief](https://www.notion.so/31d26a42061181d892f1ee9e70d57504)

**This file lives at the root of your project — not in a subfolder.**
Your AI code editor picks it up automatically from the root and reads it at the start of every session. If you move it, it loses its power.

This is the persistent instruction set for your AI builder. Think of it as the operating manual your AI builder never forgets.

Keep it updated. When something breaks repeatedly, add a rule. When a pattern works well, codify it here.

---

## Project identity

**Project name:**
<!-- What is this project called? -->

**What it does:**
<!-- One sentence. -->

**Primary user:**
<!-- Who are we building for? -->

**Current phase:**
<!-- Prototype / Product / Growth -->

---

## Codebase orientation

**Main entry point:**
<!-- e.g. src/app/page.tsx, app.py, index.js -->

**Key directories:**
<!-- Where does the important stuff live? -->

**Config files to be aware of:**
<!-- .env, config.toml, etc. -->

**Do not touch:**
<!-- Files or folders the AI builder should never modify -->

---

## How we work

**Always do this:**
-
<!-- e.g. Write a comment above every function explaining what it does -->
<!-- e.g. Check SPEC.md before adding any new feature -->
<!-- e.g. Run the linter before declaring a task done -->

**Never do this:**
-
<!-- e.g. Never install a new dependency without flagging it first -->
<!-- e.g. Never modify the database schema without updating SPEC.md -->
<!-- e.g. Never use hardcoded strings — always use the constants file -->

---

## Coding conventions

**Language / framework version:**


**Naming conventions:**
<!-- e.g. camelCase for variables, PascalCase for components -->

**File naming:**
<!-- e.g. kebab-case for all files -->

**Comment style:**
<!-- e.g. JSDoc for all exported functions -->

**Error handling:**
<!-- e.g. Always use try/catch, always log the error with context -->

---

## AI layer instructions

<!-- How should the AI builder interact with the AI layer of the product?
Define prompt patterns, output formats, fallback behaviour. -->

**Prompt format:**


**Expected output format:**


**Fallback when AI layer fails:**


---

## Debugging protocol

<!-- When something breaks, follow these steps in order. -->

1. **Reproduce** — confirm the exact input that causes the failure
2. **Isolate** — identify the smallest unit of code responsible
3. **Hypothesise** — state the most likely cause before changing anything
4. **Fix** — make the minimal change to resolve it
5. **Verify** — confirm the fix works and nothing else broke

---

## Skills available

<!-- List the skill modules available in the /skills folder.
The AI builder can reference these for specific tasks. -->

| Skill | Location | Use when |
|---|---|---|
| Example skill | `skills/example-skill/SKILL.md` | Replace with your real skills |

---

## Current known issues

<!-- Running list of bugs or rough edges. Remove when resolved. -->

-

---

## Session startup checklist

<!-- The AI builder should do this at the start of every session. -->

- [ ] Read `chapter-1/the-brief.md` — confirm the problem and user haven't changed
- [ ] Read `chapter-1/SPEC.md` — confirm current scope and phase gate
- [ ] Read `PROGRESS.md` — confirm current status and last decision
- [ ] Check this file (`agent-instructions.md`) for any new rules added since last session
- [ ] State what you plan to work on before writing any code
