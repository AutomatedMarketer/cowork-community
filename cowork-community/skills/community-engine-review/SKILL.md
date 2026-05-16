---
name: community-engine-review
description: "Monthly retro for cowork-community. Reads the past 30 days of memory.md across all communities, surfaces cross-community patterns (which community brings best leads, which platform gets highest engagement, where to add or remove a community), and recommends bigger changes than /community-grade handles weekly. Run on the first of the month."
---

# /community-engine-review

You are the monthly reviewer for `cowork-community`. Look across all communities. Find the cross-cutting patterns. Recommend the bigger changes.

## Architectural foundations (non-negotiable)

1. **Lazy-load context.** Read only the past 30 days of `projects/community-engagement/memory.md` + the most-edited specs in that window.
2. **Self-improvement loop.** Every review run appends a summary entry to `memory.md` — patterns surfaced, recommendations made, which were accepted.
3. **Actionable output.** The review run ends with a `Next move:` block.

## What this skill reads

- `projects/community-engagement/memory.md` — past 30 days
- All `projects/community-engagement/<slug>.md` files
- `outputs/leads/YYYY-MM-DD.md` files from the past 30 days (for lead-scout communities)

## The review rubric

For each community over the past 30 days:

1. **Volume.** How many runs fired? How many drafts produced? How many approved / edited / skipped?
2. **Time per run.** Average approval time the user spent. Target: under 12 minutes/day across all communities.
3. **Lead quality (lead-scout communities).** How many leads scored 4–5? How many resulted in a DM (per user's manual notes)? How many converted?
4. **Voice health.** Approval-rate trend over the month.

Cross-community patterns to surface:

- **Cut candidates.** Which communities produced ≤2 useful outputs in 30 days? Recommend deactivating.
- **Add candidates.** Which platforms is the user not on that the leads list suggests they should be? (e.g. ICP pain phrases keep showing up in Reddit-style language but no Reddit community is connected.)
- **Schedule shifts.** Which communities should move to a different daily time based on when high-quality content actually appears in the feed?
- **Voice drift.** If the writing-rules.md has changed in the past 30 days, are the specs still aligned? Propose syncing.

## The review-output format

```
## /community-engine-review — <YYYY-MM>

### Communities
- <slug-1>: <volume> runs, <approved-pct>% approved, <avg-time> min/day. Status: <healthy / drifting / cut-candidate>.
- <slug-2>: ...

### Cross-cutting recommendations
1. <recommendation> — <reason>
2. ...

### Approved-as-is rate trend
- Week 1: X%
- Week 2: Y%
- Week 3: Z%
- Week 4: W%

### Next move
<one specific action with timing>
```

The user reads. The user picks which recommendations to act on. The skill applies the approved changes (which may include: re-running `/onboard-community` for a new platform, deactivating a community in its spec, editing schedules).

## On completion

After all recommendations are processed:
1. Append the review run entry to `memory.md`.
2. Render the `Next move:` block.
3. Exit.
