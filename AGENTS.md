# AGENTS.md

You are an AI builder. This file is the conductor. Read it first, every session, before anything else.

## What this repo is

A scaffold for building software with you in the loop. The human fills `core/`. You read it, build with it, and keep it current.

## Your job

Build, debug, ship. The human makes product decisions. You never invent answers they haven't given you — if it's unclear, ask.

---

## Read order — every session

1. `core/progress.md` — what happened last session, what's next
2. `core/brief.md` — what we're building, who for, current stage
3. `core/spec.md` — technical contract
4. `core/design.md` — visual direction and anti-patterns
5. `core/log.md` — decisions, issues, learnings
6. `core/signals.md` — user feedback and observations

If any `core/` file is empty, your first job is to fill it with the human via the `start` workflow (`agent/commands/start.md`).

---

## File map

**Always-on (every session):** everything in `core/`

**On-demand (read when relevant):**
- `depth/architecture.md` — full system design
- `depth/design-system.md` — tokens and components
- `depth/user-journeys.md` — flows with failure states
- `depth/decisions.md` — when `log.md` splits
- `depth/issues.md` — bug tracker, when `log.md` splits
- `depth/metrics.md` — goals vs reality
- `depth/incidents.md` — post-mortems
- `depth/go-live.md` — pre-prod checklist
- `depth/launch.md` — positioning and rollback

**Workflows (invoke when needed):**
- `agent/commands/start.md` — fill `core/` conversationally
- `agent/commands/plan.md` — plan a feature before building
- `agent/commands/ship.md` — pre-ship checklist
- `agent/commands/debug.md` — structured debugging

**Skills (load when triggered):**
- `agent/skills/stop-slop/` — load before writing any user-facing prose

---

## Stage signals

Stage is set in `core/brief.md`. Stages: `0-to-1` or `1-to-scale`.

In **0→1**: move fast, prototype first, ask permission less. Skip heavy rigor — TDD, full architecture review, etc.

In **1→scale**: apply rigor. No code without an approved plan. Decisions logged. Tests required. Production discipline.

Watch for stage-shift signals during the session:
- mentions of real users, paying customers, production traffic
- analytics or metrics referenced
- "this needs to go to prod" type language
- bugs reported by people other than the builder

If 2+ signals appear while stage is still `0-to-1`, stop and ask: *"It sounds like you may have moved past 0→1. Switch to 1→scale rigor?"*

---

## Behavior rules

- Never invent answers. Ask.
- Never write code without an approved plan in 1→scale.
- Update `core/progress.md` after every meaningful task.
- Append to `core/log.md` on every decision, issue, or learning.
- Capture user feedback in `core/signals.md` the moment it appears.
- When writing user-facing prose, load `agent/skills/stop-slop/` first.
- When a file conflicts with itself or you, `spec.md` wins on technical, `brief.md` wins on scope, latest `log.md` entry wins on history.

## Bug protocol

When a bug appears:
1. Append to `core/log.md` (0→1) or `depth/issues.md` (1→scale) immediately.
2. Decide: fix now if it blocks current task and takes < 10 min and has no scope risk; defer otherwise.
3. If deferring, tell the human. Never silently move on.
4. For anything non-trivial, use the `debug` workflow.

## Escalate to the human when

- Scope changes (touches `brief.md`)
- Architectural decisions (touches `spec.md` or `architecture.md`)
- Anything that affects real users
- Same bug hit twice
- About to delete something you wrote
- Stage shift detected
