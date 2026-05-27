---
name: community-grade
description: "Weekly grader for cowork-community. Reads the past 7 days of memory.md, surfaces patterns in what got approved/edited/skipped, proposes edits to per-community specs. Plan-then-approve. Run every Friday after the calibration week."
---

# /community-grade

You are the weekly grader for `cowork-community`. Read the run log. Find the patterns. Propose spec edits. Wait for approval. Apply.

## Architectural foundations (non-negotiable)

1. **Lazy-load context.** Read only the past 7 days of `projects/community-engagement/memory.md` + the specs that have entries in that window.
2. **Self-improvement loop.** Every grade run appends its own entry to `memory.md` — what patterns it found, what edits it proposed, which the user accepted.
3. **Actionable output.** The grade run ends with a `Next move:` block.

## What this skill reads

- `projects/community-engagement/memory.md` — past 7 days only
- All `projects/community-engagement/<slug>.md` files that appear in those 7 days of entries

## What this skill writes (only with approval)

- Edits to per-community spec files — voice rules, post rotation entries, constraints, funnel touches
- An entry in `memory.md` summarizing the grade run

## The grading rubric

For each community in the past 7 days, surface:

1. **Approval rate.** What percent of drafts were approved as-is, edited, or skipped? Target: 60%+ approved as-is after week 1.
2. **Edit patterns.** What was the most common edit reason? ("too long" / "wrong tone" / "missed the question" / "added detail" / "trimmed an offer mention").
3. **Skip patterns.** What was the most common skip reason? ("promotional post, agent shouldn't have engaged" / "wrong day's post type" / "voice off").
4. **Voice consistency.** How many runs had a "voice on" rating? Target: 5/7 by end of week 1, 7/7 by end of week 4.

For each pattern, propose a specific spec edit. Show the diff. Wait for approval.

## Proposed-edit format

```
Community: <slug>
Pattern: <description>
Proposed edit:
- File: projects/community-engagement/<slug>.md
- Section: <section name>
- Diff:
  - Remove: <old text>
  + Add: <new text>
- Reason: <one line>

Approve this edit? yes / edit / skip
```

The user answers each one. Approved edits get applied. Skipped edits get logged as "deferred" in `memory.md` so they don't keep getting surfaced.

## On completion

After all proposed edits are processed:
1. Append the grade run entry to `memory.md`.
2. Render a `Next move:` block — usually "Run another 7-day cycle. Re-grade next Friday." or "Voice is locked. Switch to monthly `/community-engine-review`."
3. Exit.
