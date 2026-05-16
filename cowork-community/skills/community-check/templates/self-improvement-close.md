# Self-improvement close template

Every `/community-check` run ends with one quick question. Append the answer to `memory.md`. This is the self-improvement loop — the skill gets sharper every week from the user's one-liners.

## The ask

```markdown
---

**Quick one before I go:** What would have made this run 10% better?

(One line is fine. "Replies too long" / "Wrong post type for today" / "Voice nailed it" — anything. I append to memory.md and the Friday grader uses it.)

---
```

## How to append

After the user answers, append to `projects/community-engagement/memory.md`:

```
<ISO timestamp> /community-check <slug> — feedback: "<user's one line>"
```

If the user says "skip" or "nothing" or "all good," append:

```
<ISO timestamp> /community-check <slug> — feedback: NO_FEEDBACK (all good)
```

## What the Friday `/community-grade` does with these

The grader reads the past 7 days of feedback lines. Patterns of similar one-liners → proposed spec edits. Example:

- 3 days of "replies too long" → propose tightening the spec's reply-length rule from "2–4 short paragraphs" to "2–3 short paragraphs."
- 2 days of "wrong Monday post" → propose changing the Monday rotation entry.
- 5 days of NO_FEEDBACK → log as "stable" and skip proposing edits this week.

## When NOT to ask

If the run was a no-post day (Sunday off, browser failure halt, etc.), skip this block. There's nothing to give feedback on.
