---
name: capture-answers
status: published
authored_by: agent
finalised_by: hr
last_updated: 2026-10-15
---

# capture-answers: save the owner's chat answers to raw/ as a source file

## Purpose
The owner often answers questions in chat (by clicking options or typing) instead of uploading a document. Those answers are facts the brain needs to cite. This skill is the approved capture path that lets them land in `raw/`, word for word, so `ingest` can file them and pages can point at a source. It prevents two failures: facts that live only in a chat that will be forgotten, and an agent writing to `raw/` without permission.

## When invoked
- The owner has answered one or more questions in chat that settle a fact, a rule or a preference about HR content.
- Phrases: "save my answers", "record this", or any owner answer that fills a `not yet known` or `[CONFIRM]` item.

Do not invoke for preferences about how the brain writes (voice, banned phrases); those go to `instructions.md` and `log/feedback.jsonl`. Do not invoke to record anything the owner did not say.

## Procedure
1. **Collect** each question exactly as asked and the owner's answer exactly as given, including the option description shown with a clicked option.
2. **Write a new file** in `raw/` named `YYYY-MM-DD-hr-answers-<topic>.md`, with a one-line header saying when and how the answers were captured. Never append to or edit an existing `raw/` file; a later answer on the same topic gets a new file.
3. **Check** that the file holds no sensitive personal data listed in the `CLAUDE.md` hard rules. If the owner's answer contains some, stop and ask the owner to save that file themselves.
4. **Log** the run, then hand the file to `ingest`.

## Quality gate
Hard fails. Write nothing except the log line.
- An answer is summarized, reworded or inferred instead of copied.
- An existing file in `raw/` would be edited, appended to, renamed or deleted.
- The file would contain sensitive personal data.
- A question the owner did not answer is recorded as answered.

## Output
- One new file: `raw/YYYY-MM-DD-hr-answers-<topic>.md`.

## Log
```json
{"ts":"2026-10-15T16:00:00Z","actor":"claude-session","skill":"capture-answers","inputs":{"questions":2},"outputs":{"file":"raw/2026-10-15-hr-answers-lint-review.md"},"decision":"captured","notes":""}
```

## Failure modes
- **Appending to yesterday's file.** Adding new answers to an existing answers file edits `raw/`. Seen on 2026-10-15 before this skill existed. Always a new file.
