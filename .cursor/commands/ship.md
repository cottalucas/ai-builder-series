# /ship
# Pre-ship checklist. Run before marking any task complete.
# ─────────────────────────────────────────────────────
# A task is not done when the code is written.
# A task is done when a human can verify the behaviour works correctly.

## Code quality — run these first
1. `npm run typecheck` — fix all type errors before proceeding
2. `npm run lint` — fix all lint errors before proceeding
3. `npm run test` — all tests must pass

## Behaviour verification — test these manually
4. Complete the happy path for the feature you just built — does it work end-to-end?
5. Test the error states defined in SPEC.md for this feature — do they render correctly?
6. Test the edge cases from SCENARIOS.md that apply to this feature
7. Verify no console errors in the browser during normal use

## Documentation
8. Update PROGRESS.md — what was built, test results, what comes next
9. Check SPEC.md — does it still match what was built? Update if scope changed
10. If a new env variable was added: update ENV.md

## For production deploys — run GO-LIVE.md first
Before any production deployment, work through chapter-2/GO-LIVE.md completely.
Do not skip it. Every unchecked box is a risk you are knowingly accepting.

## Definition of done
A task is done when:
- All code quality checks pass
- You personally verified the behaviour works
- Error states render correctly
- PROGRESS.md is updated
- SPEC.md matches reality
