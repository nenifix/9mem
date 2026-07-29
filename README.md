# 🧠 9mem — Universal AI Agent Memory System

> **Persistent, compounding knowledge for any AI agent.**
> Inspired by [Andrej Karpathy's LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) pattern.

9mem is a **universal memory and continuity system** for AI agents — compatible with Claude, ChatGPT, Hermes, OpenCode, Cursor, and any LLM-based tool. It solves the **core problem**: every session is a clean slate. With 9mem, your agent never forgets.

Think of it like Git for your agent's brain — every task, every decision, every milestone is documented, timestamped, and cross-referenced.

---

## 🎯 The Problem

Every time you talk to an AI agent, it has **zero memory** of what came before. You repeat context, re-explain projects, and lose the thread between sessions. Tasks fall through the cracks.

## 💡 The Solution

9mem turns your agent into a **disciplined knowledge worker** that:

1. **Reads SESSION.md before every task** — so it knows exactly where you left off
2. **Documents as it works** — every milestone, every decision, every output
3. **Cross-references everything** — entities, concepts, sessions are linked
4. **Backs up to Notion** — human-readable, shareable, browsable
5. **Speaks a universal format** — any AI agent can read and write it

---

## 📁 Repository Structure

```
9mem/
├── SESSION.md              # ← THE key file. Latest session log, read first
├── SCHEMA.md               # Rules for agents — how to write, read, and maintain the wiki
├── index.md                # Master catalog — every page with a one-line summary
├── log.md                  # Chronological log — everything that happened, when
│
├── wiki/
│   ├── entities/           # People, companies, tools, places (one file each)
│   ├── concepts/           # Ideas, patterns, principles, decisions
│   └── sessions/           # Per-session transcripts and summaries
│
├── raw/                    # Source documents (immutable — agent reads, never writes)
│
└── tools/                  # Helper scripts
    └── 9mem.mdc            # Cursor/MCP configuration file
```

---

## 🚀 Quick Start

### For any AI agent, paste this into your system prompt:

```
I use 9mem — a persistent memory wiki. Before any task, read SESSION.md to
understand what was happening. At each milestone, document progress. On
completion, write a full session summary. Format: date, time, task, decisions,
outputs, next steps. Keep entities/, concepts/, and index.md updated.
```

### Agent-specific setup:

| Agent | How to activate |
|-------|----------------|
| **Claude Code** | Add SCHEMA.md instructions to CLAUDE.md |
| **ChatGPT** | Paste SCHEMA.md instructions in custom instructions |
| **Hermes / OpenCode** | Include SCHEMA.md rules in AGENTS.md |
| **Cursor** | Place `tools/9mem.mdc` in `.cursor/rules/` |
| **Any LLM** | Paste SCHEMA in system prompt or project-level context |

---

## 📋 Core Workflow

### 1️⃣ BEFORE any task → READ SESSION.md
The agent reads the latest session log to understand context, current state, and what was happening.

### 2️⃣ DURING work → DOCUMENT milestones
At every significant checkpoint:
- What was accomplished
- Decisions made
- Files changed
- Blockers encountered

### 3️⃣ ON COMPLETION → WRITE session summary
Append to `log.md`, update `wiki/sessions/`, update `index.md`

### 4️⃣ BACKUP → Sync to Notion
Key sessions and wiki pages are mirrored to Notion for human browsing.

---

## 🧩 Schema Principles

1. **Date-time stamp everything** — `YYYY-MM-DD HH:MM TZ` on every entry
2. **One entity per file** — `wiki/entities/nenifix.md`, `wiki/entities/kofifix.md`
3. **One concept per file** — `wiki/concepts/llm-wiki.md`, `wiki/concepts/9mem.md`
4. **Cross-reference with `[[wikilinks]]`** — Obsidian-compatible `[[page-name]]` format
5. **Consistent prefixes in log** — `## [2026-07-29] task | Description` — grep-parseable
6. **Append-only log** — never edit history, just add
7. **index.md is source of truth for navigation** — update on every change

---

## 🔄 Sync Targets

- **Local**: `9mem/` directory (git-tracked)
- **GitHub**: `github.com/nenifix/9mem` (version history, collaboration)
- **Notion**: Human-readable backup (optional)
- **Obsidian**: Open directly as a vault (optional)

---

## 📜 License

MIT — free for anyone to use, fork, and adapt.

---

## 👤 Author

**Nine (Godwin Appiah)** — Founder of Nenifix
