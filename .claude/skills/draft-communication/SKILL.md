---
name: draft-communication
description: Draft a formal HR communication (staff announcement, manager memo, policy notice) from facts already in the wiki, with unknowns left as [CONFIRM] placeholders. Drafts only, never sends. Triggers on "draft an announcement", "write a memo", "write to staff about", "prepare a notice".
---

# draft-communication (wrapper)

This is a thin wrapper. The procedure lives in the brain itself so every agent reads the same file.

1. Read `CLAUDE.md` and `instructions.md` if you have not this session.
2. Follow `skills/draft-communication.md` exactly, including its quality gate.
3. Append the run to `log/runs.jsonl` with an `actor` field.

If this wrapper and `skills/draft-communication.md` ever disagree, the skill file wins.
