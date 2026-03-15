# AI Builder Series — Executable Scaffold

This repo is the executable layer behind the [AI Builder Series](https://www.notion.so/31d26a42061181d7a341f5f25c0ff028) by Lucas Cotta.

The series is a three-chapter public framework guiding builders from idea → prototype → product → growth, using AI tools as leverage.

This repo is the thing you clone and fill in. The Notion chapters explain the thinking. These files are where you do the work.

---

## How to use this repo

**Clone it directly into your project root:**
```bash
git clone https://github.com/cottalucas/ai-builder-series.git .
```

Or clone it standalone and copy the files into your existing project root.

**Then:**
1. Open the project in your AI code editor
2. Fill in `agent-instructions.md` first — it lives at root and your AI builder reads it automatically every session
3. Fill in `chapter-1/the-brief.md` and `chapter-1/SPEC.md` before writing any code
4. Start building — your AI builder uses these files as live context
5. Come back to `chapter-2/` when you have real users and a validated direction
6. Come back to `chapter-3/` when you're ready to grow

**A complete `chapter-1/` is enough to ship an MVP.** The chapter-2 and chapter-3 files sit quietly in their folders until you need them. No friction, no dependency.

> The `skills/` folder also lives at root. Add skill modules as you identify repeatable tasks your AI builder needs to handle consistently.

---

## Structure

```
your-project/                   # ← clone into here
│
├── agent-instructions.md       # AI builder operating manual — ROOT LEVEL, always
├── PROGRESS.md                 # Where you are across all three chapters
├── .gitignore                  # Sensible defaults pre-configured
│
├── chapter-1/                  # The Prototype Brief — start here
│   ├── the-brief.md            # Your idea, problem, user, and constraints
│   └── SPEC.md                 # Technical spec for your prototype
│
├── chapter-2/                  # The Product Brief — when prototype is validated
│   ├── PRD.md                  # Product requirements document
│   ├── ARCHITECTURE.md         # Technical architecture
│   ├── SCENARIOS.md            # Edge cases and holdout scenarios
│   ├── user-journeys.md        # Core user flows
│   └── design-brief.md        # Visual and UX direction
│
├── chapter-3/                  # The Growth Brief — when you're ready to scale
│   ├── LAUNCH.md               # Launch strategy and GTM plan
│   ├── task-list.md            # Prioritised execution tasks
│   └── implementation-plan.md # Phased rollout and milestones
│
└── skills/                     # Reusable AI skill modules
    ├── README.md               # What skills are and how to add them
    └── example-skill/
        └── SKILL.md            # A filled-in example to copy from
```

---

## Chapter map

| Chapter | Notion | When to use |
|---|---|---|
| Chapter 1 — The Prototype Brief | [Open](https://www.notion.so/31d26a42061181d892f1ee9e70d57504) | Day one. Always. |
| Chapter 2 — The Product Brief | [Open](https://www.notion.so/31d26a420611813499bfe07c988c97ac) | After you have real users and validated direction |
| Chapter 3 — The Growth Brief | [Open](https://www.notion.so/31d26a42061181eba81fd97093010d90) | When you're ready to scale distribution and retention |

---

## Philosophy

- **Tool-agnostic** — no specific tools are prescribed. The files work with any AI code editor, any stack.
- **Progressive** — each chapter builds on the last, but each is independently useful.
- **AI-native** — every file is written to be read by both you and your AI builder as live context.
- **Specific beats generic** — placeholder guidance is instructional, not decorative.

---

## Skills

The `skills/` folder holds reusable instruction modules your AI builder can reference for specific tasks (generating PDFs, parsing documents, writing emails, etc.). See `skills/README.md` for how to create and use them.

---

*Part of the [AI Builder Series](https://www.notion.so/31d26a42061181d7a341f5f25c0ff028) by Lucas Cotta*
