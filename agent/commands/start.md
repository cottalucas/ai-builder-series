# Command: start

> Conversationally fill `core/` files with the human. Run this when any `core/` file is empty or when the human invokes `/start`.

## How to run

1. Greet the human. Confirm you'll walk them through filling `core/`.
2. Work through the files in this order: `brief.md` → `spec.md` → `design.md`. Skip what's already filled.
3. For each file, ask **one question at a time**. Prefer multiple-choice when possible.
4. After each section, show them what you've written and ask for approval before moving on.
5. Save updates to the file as you go — don't wait until the end.
6. When `brief.md`, `spec.md`, and `design.md` are filled, stop. The human can start building.

## Rules

- Don't ask about `progress.md`, `log.md`, or `signals.md` — those fill themselves as the work happens.
- Don't suggest values they didn't give you. If you need a default, label it as a suggestion and confirm.
- Keep questions short. One per message.
- If they say "I don't know," offer 2-3 options or skip the field and flag it as open.

## Stop conditions

- Human says "stop" or "let's build" — save what you have, move on.
- A `core/` file is non-trivially filled — assume the human did it manually, skip.
