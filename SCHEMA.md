# 📐 9mem Schema — Agent Behavior Rules

> This file defines how AI agents should read, write, and maintain the 9mem wiki.
> Copy this into your agent's system prompt, CLAUDE.md, AGENTS.md, or custom instructions.

---

## 🟢 MANDATORY BEHAVIOR

### Rule 1: Read SESSION.md before every task
Always start by reading `SESSION.md`. It tells you:
- What was happening before this session
- What's in progress
- What the last state was

### Rule 2: Document at every milestone
Whenever you complete a significant step:
1. Write what happened in `log.md` (append only)
2. Update `SESSION.md` with current state
3. Update `index.md` if new pages were created

### Rule 3: Timestamp everything
Every entry uses this format:
```
## [YYYY-MM-DD HH:MM UTC] action | Description
```

### Rule 4: Use wikilinks
Link entities and concepts using `[[wikilinks]]`:
- `[[nenifix]]` → wiki/entities/nenifix.md
- `[[llm-wiki]]` → wiki/concepts/llm-wiki.md

### Rule 5: Append-only log
Never edit past log entries. The log is immutable history. Only SESSION.md gets rewritten (it's the live state).

### Rule 6: One entity, one file
Each person, company, tool, or project gets its own file in `wiki/entities/`.
Each concept, pattern, or principle gets its own file in `wiki/concepts/`.

### Rule 7: Every session gets a wiki page
After each session, write `wiki/sessions/YYYY-MM-DD.md` with:
- Participants
- Tasks worked
- Decisions made
- Files/outputs
- Next steps

---

## 📋 Workflow Steps

### STARTUP (first thing every session)
1. Read `SESSION.md` (or `log.md` last 5 entries if no SESSION.md)
2. Read relevant entity/concept pages via wikilinks
3. Respond with summary of where things left off

### DURING WORK
At each milestone:
1. Note what was accomplished
2. Note decisions made
3. Note blockers
4. Write to `SESSION.md` with current state

### TASK COMPLETION
1. Write session summary to `wiki/sessions/YYYY-MM-DD.md`
2. Append to `log.md`
3. Update relevant entity pages
4. Update concept pages if new insights
5. Update `index.md`
6. Rewrite `SESSION.md` with final state
7. Back up key entries to Notion (optional)

### QUERY
When asked "what was I doing?" or "where were we?":
1. Read `SESSION.md`
2. Read last 3 entries of `log.md`
3. Read relevant wiki pages
4. Compose full context report

---

## File Format Standards

### Entity pages (`wiki/entities/X.md`)
```markdown
# Entity Name

**Type:** person | company | tool | project | location
**Status:** active | paused | archived | completed
**Last updated:** YYYY-MM-DD

## Summary
Brief description.

## Details
- Key fact 1
- Key fact 2

## Relationships
- [[related-entity-1]] — relationship description

## Session References
- [[YYYY-MM-DD]] — what happened in that session
```

### Concept pages (`wiki/concepts/X.md`)
```markdown
# Concept Name

**Status:** active | draft | evolving
**Last updated:** YYYY-MM-DD

## Summary
What this concept is.

## Details
Deep explanation.

## Related
- [[related-entity]]
- [[related-concept]]

## Session References
- [[YYYY-MM-DD]] — when this was discussed
```

### Session pages (`wiki/sessions/YYYY-MM-DD.md`)
```markdown
# Session: YYYY-MM-DD

**Start:** HH:MM UTC
**End:** HH:MM UTC
**Participants:** [names]

## Tasks
1. Task description — status: ✅ | 🟡 | ❌

## Decisions
- Decision 1

## Outputs
- File: path/to/file

## Next Steps
- [ ] Step 1
```

---

## Agent-Specific Integration

### Claude Code
Add to `CLAUDE.md`:
```
Before any task, read SESSION.md. Document milestones. On completion, write session summary.
```

### ChatGPT
Add to Custom Instructions:
```
[9MEM ACTIVE] I maintain a persistent wiki. Before responding, read SESSION.md. At milestones, log progress. Always timestamp.
```

### Hermes / OpenCode
Add to `AGENTS.md` or system prompt:
```
9MEM: Read SESSION.md first. Write milestones. End with log.md entry.
```

### Cursor
Place `tools/9mem.mdc` in `.cursor/rules/` directory.

### Any tool
Paste SCHEMA.md content as system prompt or project context.

---

## Principles

- **Write for humans AND machines** — markdown is readable by both
- **Append, don't edit** — log.md is immutable history
- **Cross-reference everything** — wikilinks make the wiki a graph, not a pile
- **Track the "why"** — not just what was done, but why decisions were made
- **Be concise** — one line per log entry, one page per entity
- **Never lose context** — before any costly operation, check the wiki first
