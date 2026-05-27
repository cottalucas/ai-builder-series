# Command: plan

> Plan a feature before building. Run before any non-trivial work in 1→scale. Optional but recommended in 0→1.

## How to run

1. Confirm what's being planned. One sentence.
2. Check `core/brief.md` — is this in scope? If not, escalate.
3. Check `core/log.md` (or `depth/decisions.md`) — have we discussed this before?
4. Check `core/spec.md` (or `depth/architecture.md`) — what does it touch?
5. Propose 2-3 approaches with trade-offs. Lead with your recommendation.
6. Wait for the human to pick.
7. Break the chosen approach into tasks. Each task: file path, what changes, how to verify.
8. Show the plan. Get explicit approval before any code.

## Rules

- No code in this step. Plan only.
- Tasks should be 2-5 minutes of focused work each.
- Every task has a verification step — how do we know it worked.
- If the plan touches `spec.md` or `architecture.md`, flag it as a decision and log to `core/log.md`.
