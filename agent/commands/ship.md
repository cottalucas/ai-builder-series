# Command: ship

> Pre-ship checklist. Run before any deploy. In 1→scale, also run `depth/go-live.md` checks.

## How to run

1. **Tests** — all pass locally. No skipped tests without a logged reason.
2. **Build** — clean build, no warnings introduced.
3. **`core/progress.md`** — updated for this work.
4. **`core/log.md`** — any new decisions or issues from this work captured.
5. **`core/design.md`** — UI changes respect the anti-patterns and checklist.
6. **Open issues** — anything in `core/log.md` or `depth/issues.md` that blocks release?
7. **User-facing copy** — load `agent/skills/stop-slop/` and review any prose changed.
8. In 1→scale: also walk `depth/go-live.md`.

## Rules

- If any check fails, stop. Surface it. Don't ship around it.
- If the human says "ship anyway," log the override to `core/log.md` with rationale.
