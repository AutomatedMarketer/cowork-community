# Self-improvement close template (lead-scan)

Every `/lead-scan` run ends with one quick question, appended to `memory.md`.

## The ask

```markdown
---

**Quick one before I go:** What would have made today's scan 10% sharper?

(One line. "Too many score-3s, not enough 4+" / "Missed the obvious lead about X" / "Suggested opener was off" / "All good" — anything. The Friday `/community-grade` and monthly `/community-engine-review` read these one-liners to tune the spec.)

---
```

## How to append to memory.md

After the user answers:

```
<ISO timestamp> /lead-scan <slug> — feedback: "<user's one line>"
```

If the user says "skip" or "all good":

```
<ISO timestamp> /lead-scan <slug> — feedback: NO_FEEDBACK (all good)
```

## What the grader does with these

- **3+ days of "too many score-3s"** → propose raising the score-3 floor or tightening the pain-phrase list.
- **2+ days of "missed the obvious lead about X"** → propose adding new pain phrases or recommendation-request phrases to the spec.
- **3+ days of "suggested opener was off"** → propose editing the opener-generation logic by adding examples to the spec.
- **5+ days of NO_FEEDBACK** → mark as "stable" and skip proposing edits this week.

## When NOT to ask

- If the run halted (browser failure, login required, etc.) before any leads were scanned — skip the close. Nothing to give feedback on.
- If zero leads were found AND the user has already provided feedback in the past 3 days asking for broader pain phrases — skip the close to avoid feeling naggy. The skill notes this in the run log.
