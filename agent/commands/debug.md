# Command: debug

> Structured debugging. Use for anything non-trivial. The temptation to guess is the signal you need this.

## How to run

1. **Reproduce** — get a reliable way to make the bug happen. If you can't reproduce, you can't fix.
2. **Isolate** — narrow the surface. What's the smallest change or input that triggers it?
3. **Hypothesize** — state what you think is happening, in writing, before testing.
4. **Test** — verify the hypothesis. If wrong, go back to step 3 with new info.
5. **Fix** — make the minimal change that resolves the root cause, not the symptom.
6. **Verify** — confirm the fix in the original repro. Then confirm nothing adjacent broke.
7. **Log** — append to `core/log.md` (0→1) or `depth/issues.md` (1→scale). What it was, what fixed it.

## Rules

- Never claim a fix without reproducing the bug, then reproducing the fix.
- If the same bug hits twice, escalate to the human — the root cause is deeper than you think.
- No "should work" without verification. Verify or say it's unverified.
