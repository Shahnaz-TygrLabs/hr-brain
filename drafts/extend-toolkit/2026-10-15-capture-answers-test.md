# Test run: capture-answers

**Gap sentence:** the owner's chat answers had to be saved as sources, and no approved skill could write them to raw/, so claude-session wrote two raw files without an approved writer (lint finding B, drafts/lint/2026-10-15-lint.md).

**Duplicate check:** ingest reads raw/ but never writes it; draft-communication writes drafts/ only. No existing skill covers this.

**Test input:** the owner's answers to the lint review questions.

**Test output** (written here, not to raw/, while the skill is a draft). It would be saved as raw/2026-10-15-hr-answers-lint-review.md:

> # HR Team answers on the lint review
>
> Captured 2026-10-15 from the HR Team's multiple-choice answers in a Claude session. Recorded verbatim.
>
> - Q: Issue A: fix the memo's Mettl test-length line?
>   A: "Leave it" (option description: "Keep the memo as it is.")
> - Q: Issue B: how should your chat answers be saved from now on?
>   A: "Approve & make a skill (Recommended)" (option description: "Keep the two files as they are, and I'll create a 'capture answers' skill so saving your chat answers becomes an approved step.")

**Gate results:**
- Answers copied word for word, with option descriptions: pass.
- New file only, no existing raw/ file touched: pass.
- No sensitive personal data: pass.
- No unanswered question recorded as answered: pass.

**Status:** draft, awaiting owner finalization.
