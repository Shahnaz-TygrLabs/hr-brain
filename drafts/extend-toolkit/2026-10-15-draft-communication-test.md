# Test run: draft-communication

**Gap sentence:** the owner asked for a staff holiday announcement and no skill covered drafting communications from wiki facts, so the work would otherwise have been improvised.

**Duplicate check:** ingest writes wiki pages only; lint-brain writes lint reports only. No overlap.

**Test input:** wiki/policies/holidays-2026.md, audience all staff, type announcement.

**Test output:** drafts/announcements/2026-10-15-holiday-calendar-2026.md

**Gate results:**
- Every statement traces to a wiki fact: pass.
- Unknowns shown as [CONFIRM] placeholders (company name, office mapping, asterisk meaning, weekend policy, issue date): pass.
- No sensitive personal data: pass.
- No banned phrases or characters (checked with a search for em-dashes and exclamation marks): pass.
- Written to drafts/ only, nothing sent: pass.

**Learned:** 14 of 17 dates had already passed on the test date. Added "Stale timing" to the skill's failure modes.

**Status:** draft, awaiting owner finalization.
