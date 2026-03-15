# AI Builder Series — Executable Scaffold

The executable layer behind the [AI Builder Series](https://www.notion.so/31d26a42061181d7a341f5f25c0ff028) by Lucas Cotta.

Clone it. Fill it in. Drop it into Cursor. Build.

---

## Setup

```bash
git clone https://github.com/cottalucas/ai-builder-series.git .
```

---

## Fill order — do this exactly

This is not optional. The files are designed to be filled in this sequence.
Skip a step and your AI builder will invent answers you didn't give it.

### MVP (Chapter 1 only — enough to ship a prototype)

| Step | File | What you're doing | Time |
|---|---|---|---|
| 1 | `.cursor/rules/project.md` | Name your project. One sentence on what it does. | 5 min |
| 2 | `.cursor/rules/stack.md` | Commit to your tech stack. | 10 min |
| 3 | `chapter-1/the-brief.md` | Define the problem, user, scope, constraints. | 1–2 hrs |
| 4 | `chapter-1/SPEC.md` | Define the technical contract — data model, flows, phase gates. | 1–2 hrs |
| 5 | **Build** | First prompt: *"Read SPEC.md and .cursor/rules/. Write your build plan before any code."* | — |
| 6 | `PROGRESS.md` | Your AI builder updates this after every task. You update the status fields. | Ongoing |

### Product (Chapter 2 — after prototype is validated)

| Step | File | What you're doing |
|---|---|---|
| 7 | `chapter-2/PRD.md` | Document what prototype taught you. Define the real product. |
| 8 | `chapter-2/ARCHITECTURE.md` | Full system design — data model, security, testing, what breaks first. |
| 9 | `chapter-2/user-journeys.md` | Every critical flow with failure states. |
| 10 | `chapter-2/design-brief.md` | Visual direction — colours, typography, component patterns. |
| 11 | `chapter-2/SCENARIOS.md` | Edge cases. **Keep this in a separate repo — your AI builder must never see it.** |

### Growth (Chapter 3 — when product is live and metrics are running)

| Step | File | What you're doing |
|---|---|---|
| 12 | `chapter-3/LAUNCH.md` | Positioning, channels, launch sequence, rollback criteria. |
| 13 | `chapter-3/task-list.md` | Live execution tasks with acceptance criteria. |
| 14 | `chapter-3/implementation-plan.md` | Growth phases, loops, metrics, eval cycle. |

---

## File map

```
your-project/
│
├── .cursor/
│   ├── rules/
│   │   ├── project.md        ← FILL FIRST. Project name, what it does, phase.
│   │   ├── stack.md          ← FILL SECOND. Tech stack, commands, conventions.
│   │   ├── workflow.md       ← Pre-filled. Phase gates, session rules, debug protocol.
│   │   └── known-issues.md  ← Live bug log. You and AI builder both update this.
│   ├── commands/
│   │   ├── plan.md           ← /plan — plan before building any feature
│   │   ├── ship.md           ← /ship — pre-ship checklist
│   │   └── debug.md         ← /debug — structured debugging protocol
│   └── plans/               ← AI builder saves plans here (Shift+Tab in Cursor)
│
├── ENV.md                   ← Environment variables map. Fill alongside SPEC.md.
├── PROGRESS.md              ← AI builder writes here after every task. You own the status fields.
│
├── chapter-1/               ← The Prototype Brief. Fill before writing any code.
│   ├── the-brief.md         ← Problem, user, solution, scope, constraints, success signal.
│   └── SPEC.md              ← Stack, data model, flows, security, testing, phase gates.
│
├── chapter-2/               ← The Product Brief. Fill after prototype is validated by real users.
│   ├── PRD.md               ← Validated problem, vision, features, metrics.
│   ├── GO-LIVE.md           ← Pre-production checklist. Run before every prod deploy.
│   ├── ARCHITECTURE.md      ← Full system design, security, testing, bottlenecks.
│   ├── SCENARIOS.md         ← Edge cases. Keep in a SEPARATE REPO — AI never sees this.
│   ├── user-journeys.md     ← Core flows with failure states.
│   └── design-brief.md     ← Colours, typography, component patterns, layout.
│
├── chapter-3/               ← The Growth Brief. Fill when product is live and metrics are running.
│   ├── LAUNCH.md            ← Positioning, channels, launch sequence, rollback criteria.
│   ├── task-list.md         ← Live tasks with acceptance criteria. AI builder updates status.
│   └── implementation-plan.md ← Growth phases, loops, metrics, eval cycle.
│
└── skills/                  ← Domain-specific knowledge modules loaded on demand.
    ├── README.md            ← How to create and use skills.
    └── example-skill/
        └── SKILL.md         ← Filled-in example. Copy and adapt.
```

---

## How it works in Cursor

**`.cursor/rules/`** — Cursor reads all files here automatically at the start of every session. No prompt needed. These replace the single `agent-instructions.md` file — modular, focused, easier to maintain.

**`.cursor/commands/`** — Type `/plan`, `/ship`, or `/debug` in the Cursor agent input to run these workflows. Add your own as you discover repeatable patterns.

**`SPEC.md`** — The contract. Your AI builder builds what this document says. If the code drifts from the spec, the spec wins — update the code, not the spec.

**`PROGRESS.md`** — The session handoff. Your AI builder writes here after every task so the next session knows exactly where to pick up. Without this, every session starts from zero.

**`skills/`** — Domain knowledge loaded on demand. Different from rules — not always-on. Use for things like Swiss tax law, a complex output format, or a specific API integration pattern.

---

## Progressive adoption

Chapter 1 is enough to ship an MVP. Chapters 2 and 3 sit quietly until you need them.

| Chapter | Notion | When |
|---|---|---|
| 1 — The Prototype Brief | [Open →](https://www.notion.so/31d26a42061181d892f1ee9e70d57504) | Day one |
| 2 — The Product Brief | [Open →](https://www.notion.so/31d26a420611813499bfe07c988c97ac) | After 5+ real users validate the prototype |
| 3 — The Growth Brief | [Open →](https://www.notion.so/31d26a42061181eba81fd97093010d90) | After product is live and metrics are instrumented |

---

## Tool note

This repo is built for Cursor. The `.cursor/` folder uses Cursor's native rules, commands, and plans system.

If you use a different AI code editor, the concepts are the same — adapt the `.cursor/` folder to your tool's equivalent (e.g. `.github/copilot-instructions.md` for Copilot, `CLAUDE.md` for Claude Code). The chapter files work with any tool.

---

*Part of the [AI Builder Series](https://www.notion.so/31d26a42061181d7a341f5f25c0ff028) by Lucas Cotta*
*[github.com/cottalucas/ai-builder-series](https://github.com/cottalucas/ai-builder-series)*
