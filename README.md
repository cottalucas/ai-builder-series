# AI Builder Series

An opinionated scaffold for building software with AI agents — from idea to live, measured, and compounding.

The companion to the [AI Builder Series](https://www.notion.so/31d26a42061181d7a341f5f25c0ff028) framework by Lucas Cotta.

---

## What this is

A clone-and-fill repo that gives your AI agent the artifacts it needs to build with you, not at you. The structure separates what's always true about your product (`core/`) from what becomes true as you scale (`depth/`), and tells the agent how to use it all (`AGENTS.md`).

It is tool-agnostic. The agent reads `AGENTS.md` and routes itself. Cursor users get slash commands via a thin adapter; other tools work directly with the universal scaffold.

## Quickstart

```bash
git clone https://github.com/cottalucas/ai-builder-series.git my-project
cd my-project
```

Open the project in your AI editor. The agent reads `AGENTS.md` and walks you through filling `core/`.

If you're on Cursor, type `/start` to begin.

## How it works

The agent reads `AGENTS.md` first. That file is the conductor — it tells the agent what to read, when, and how files relate.

Your job is to fill in `core/`. The agent's job is to use what you've filled in to build, debug, ship, and remember.

| Folder | Purpose |
| --- | --- |
| `core/` | Living product artifacts. Always exists. Read every session. |
| `depth/` | Added when complexity demands it. Most users never touch this. |
| `agent/` | Behavior layer — commands and skills the agent uses. |
| `.cursor/` | Thin Cursor adapter. Other tools work without it. |

## Two stages

You're either in **0→1** or **1→scale**. Set it in `core/brief.md` and the agent will adapt — moving faster and asking less in 0→1, applying more rigor in 1→scale. The agent watches for stage-shift signals and flags drift.

## Use with other tools

This scaffold is built on `AGENTS.md` — an emerging convention supported by Cursor, Claude Code, Codex, Gemini CLI, and others. The core scaffold works anywhere markdown does. Cursor-specific niceties (slash commands) live in `.cursor/` and can be ignored on other tools.

## Credits

Stop-Slop skill by [Hardik Pandya](https://github.com/hardikpandya/stop-slop), MIT licensed and used with attribution. See [`CREDITS.md`](CREDITS.md).

## License

MIT — see [`LICENSE`](LICENSE).

---

*Part of the [AI Builder Series](https://www.notion.so/31d26a42061181d7a341f5f25c0ff028) by Lucas Cotta.*
