---
name: draft-communication
status: published
authored_by: agent
finalised_by: hr
last_updated: 2026-10-15
---

# draft-communication: draft a formal HR communication from what the wiki knows

## Purpose
Turn facts already filed in `wiki/` into a ready-to-review HR communication: a staff announcement, a manager memo or a policy notice. It prevents two failures: a draft that states things the brain does not know, and a draft that leaks private employee data or reads as legal advice.

## When invoked
- The owner asks for an announcement, notice, memo, email or letter built from wiki content.
- Phrases: "draft an announcement", "write a memo", "write to staff about", "prepare a notice".

Do not invoke when the topic has no wiki page yet; run `ingest` on the source first. Do not invoke to send anything; this skill only drafts.

## Procedure
1. **Confirm the brief.** Required: topic, audience, and communication type. A missing item is asked for, never guessed.
2. **Read the sources.** Read the relevant wiki pages and their raw files. Every statement in the draft must trace to a **fact** on a wiki page.
3. **Handle gaps visibly.** Anything the wiki marks `not yet known`, `assumption` or `needs legal check` appears in the draft as a bracketed `[CONFIRM: ...]` placeholder, never as a filled-in answer.
4. **Write** in the voice from `instructions.md` (formal, precise, US English) and readable by a manager outside HR.
5. **Check** the draft against the hard rules in `CLAUDE.md` and the banned phrases in `instructions.md`.
6. **Attach a review note** under the draft, separated by a rule: sources used, every `[CONFIRM]` item, and anything checked by hand.
7. **Write** the draft to `drafts/<type>/YYYY-MM-DD-<slug>.md` and log the run.

## Quality gate
Hard fails. Write nothing except the log line.
- A statement in the draft has no source on a wiki page.
- An unknown, assumption or legal question is presented as settled.
- The draft contains sensitive personal data listed in the `CLAUDE.md` hard rules.
- The draft contains a banned phrase or character from `instructions.md`.
- The draft is written anywhere outside `drafts/`, or anything is sent.

## Output
- `drafts/<type>/YYYY-MM-DD-<slug>.md`: the draft, then a review note.

## Log
```json
{"ts":"2026-10-15T14:30:00Z","actor":"claude-session","skill":"draft-communication","inputs":{"pages":["wiki/policies/holidays-2026.md"],"audience":"all staff"},"outputs":{"draft":"drafts/announcements/2026-10-15-holiday-calendar-2026.md","confirm_items":4},"decision":"drafted","notes":""}
```

## Failure modes
- **Stale timing.** A calendar or deadline is announced after most of its dates have passed. Check the dates against today and tell the owner.
