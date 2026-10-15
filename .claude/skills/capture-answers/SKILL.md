---
name: capture-answers
description: Save the owner's chat answers word for word as a new source file in raw/, so ingest can file them and wiki pages can cite them. Never edits an existing raw file. Triggers on "save my answers", "record this", or an owner answer that settles a not-yet-known or CONFIRM item.
---

# capture-answers (wrapper)

This is a thin wrapper. The procedure lives in the brain itself so every agent reads the same file.

1. Read `CLAUDE.md` and `instructions.md` if you have not this session.
2. Follow `skills/capture-answers.md` exactly, including its quality gate.
3. Append the run to `log/runs.jsonl` with an `actor` field.

If this wrapper and `skills/capture-answers.md` ever disagree, the skill file wins.
