# Next move block template

Every `/community-check` run ends with this block. Subject + Verb + Timing + Why. Specific. Actionable. Time-bound.

```markdown
---

## ⚡ Next move

**Subject:** {{WHAT — e.g. "The 2 edited replies from today's run"}}
**Verb:** {{ACTION — e.g. "Re-read in `<community>` to confirm the edits posted correctly"}}
**Timing:** {{WHEN — e.g. "Within the next 30 minutes"}}
**Why:** {{REASON — e.g. "Edits sometimes don't save on first click; this catches it before it festers"}}

---
```

## Examples by run outcome

### High-approval run (8/10 approved as-is, 2 edited)
- Subject: The 2 edited replies
- Verb: Re-read in the community to confirm the edits posted correctly
- Timing: Within the next 30 minutes
- Why: Edits sometimes don't save on first click; catch it before it festers

### Low-approval run (3/10 approved, 5 edited heavily, 2 skipped)
- Subject: The voice
- Verb: Open `about-me/writing-rules.md` and add 3 specific examples of what you'd write differently
- Timing: Tonight before bed
- Why: A 50% edit rate means the agent's voice model is drifting; richer writing-rules sharpens tomorrow's drafts

### Voice-off run (drafts felt off across the board)
- Subject: This run's drafts
- Verb: Reply to me here with one line of why it felt off, and run `/community-grade` Friday
- Timing: Now (one line) + Friday (full grade)
- Why: Patterns will be clearer in 5 more days of data; the grader edits the spec from those patterns

### No-posts day (Sunday off / new community / browser issue)
- Subject: Tomorrow's run
- Verb: Watch the scheduled run fire at `<time>` and approve drafts then
- Timing: `<tomorrow_date>` at `<time>`
- Why: Tomorrow is the first real engagement day — the schedule needs to fire successfully to lock in the rhythm
```

## How to pick

After every run, the skill picks the right Next move shape based on the run's stats. The picks above are defaults. The skill can adapt to surface a specific lever the user controls — never "let me know if you need anything" (that's not a next move).
