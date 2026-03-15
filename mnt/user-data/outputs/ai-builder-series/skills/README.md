# skills/

> Notion reference: [Chapter 1 — The Prototype Brief](https://www.notion.so/31d26a42061181d892f1ee9e70d57504)

## What is a skill?

A skill is a reusable instruction module that teaches your AI builder how to do a specific, repeatable task — generating a PDF report, parsing a document, sending a formatted email, calling an external API, and so on.

Instead of explaining the task in every prompt, you write the instructions once in a `SKILL.md` file. Your AI builder reads it at the start of the relevant task and follows it consistently.

Skills are the memory your AI builder doesn't have by default.

---

## When to create a skill

Create a skill when:
- You find yourself explaining the same task more than once
- A task has specific rules, edge cases, or output formats that must be consistent
- A task involves an external tool or library with a specific usage pattern
- You want the AI builder to follow a pattern you've tested and know works

---

## How skills work in practice

1. You create a folder inside `skills/` — e.g. `skills/pdf-report/`
2. Inside that folder, you write a `SKILL.md` that explains the task
3. In your `agent-instructions.md`, you reference the skill in the skills table
4. When you want the AI builder to use it, you say: *"Read the skill at `skills/pdf-report/SKILL.md` and use it to generate the output"*

That's it. The AI builder reads the file and follows the instructions.

---

## Skill folder structure

```
skills/
├── README.md                  ← this file
├── example-skill/
│   └── SKILL.md               ← a filled-in example to copy from
└── your-skill-name/
    └── SKILL.md               ← your skill
```

You can optionally include supporting files in the skill folder:
- Sample input files the skill processes
- Template files the skill outputs
- A `test/` subfolder with test cases

---

## How to write a SKILL.md

See `example-skill/SKILL.md` for a complete example.

The structure is:
1. **What this skill does** — one sentence
2. **When to use it** — the trigger condition
3. **Inputs** — what the AI builder needs before it starts
4. **Steps** — the exact instructions to follow
5. **Output format** — what done looks like
6. **Edge cases** — what to do when something unexpected happens
7. **Example** — a short worked example

---

## Tips

- Write skills for yourself, not for the internet. They can be rough and specific.
- A skill that's too long is worse than no skill. Keep it to what's essential.
- Test your skill on a real task before committing it. If it doesn't work, fix the skill.
- Skills can reference other skills. Keep each skill focused on one task.
