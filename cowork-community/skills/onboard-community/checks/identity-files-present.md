# Check — Identity files present

## Purpose

Verify that `cowork-ai-os` has been onboarded before this wizard runs. The wizard reads three identity files. If any is missing or empty, halt.

## Files to check

| File | Required content (minimum) |
|---|---|
| `about-me/about-me.md` | Non-empty. Should describe the user's role, business, working style. |
| `about-me/business-brain.md` | Non-empty. Must contain at least one offer + an ICP one-liner + at least 3 pain phrases. (Pain phrases are required for `lead-scout` mode.) |
| `about-me/writing-rules.md` | Non-empty. Must contain at least tone + banned-phrase list. |

## Pass criteria

All three files exist, are non-empty, and contain the minimum content described above.

## Fail handling

If a file is missing:

> "Halt: `<file>` is missing. Run `/onboard` from cowork-ai-os to create it. I'll be here when you finish."

If a file exists but is empty:

> "Halt: `<file>` exists but is empty. Run `/onboard` Phase <N> from cowork-ai-os to fill it. (Phase 2 = about-me, Phase 3 = business-brain, Phase 4 = writing-rules.)"

If `business-brain.md` lacks 3+ pain phrases AND the user wants to add any `lead-scout` community:

> "Lead-scout mode needs at least 3 ICP pain phrases in `business-brain.md`. I see <N>. Add <3 - N> more, then re-run me. Founder-only communities can proceed."

If the user only adds `founder` communities, the pain-phrase rule does not apply — proceed.

## Skip-not-allowed

This check cannot be skipped or overridden. The wizard genuinely cannot proceed without these files — every later step reads from them.
