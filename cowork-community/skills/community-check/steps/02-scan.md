# Step 2 — Scan the last 24 hours

## What this step does

Scan the community feed for posts from the last 24 hours. Identify 4 priority types in this order.

## Inputs

- Spec file: full content (constraints, voice rules, what to skip)
- Last run's timestamp from `memory.md` (so the agent knows what's "since last run" if not exactly 24h)

## What to identify

Scan in this priority order:

1. **Unanswered member questions.** Posts that ask a question and have zero replies (or only off-topic / team-bot replies). HIGHEST priority — reply to ALL of them.
2. **Posts with team replies but no founder reply.** Team members may have answered, but the user (founder) hasn't shown up. Add founder presence.
3. **New member introductions.** First-time posters / level-1 / "say hi" posts. Welcome briefly. Keep it warm and short.
4. **Member wins or milestones.** Someone hit a goal, finished a course, made a sale. Celebrate and push to the next step.

## What to SKIP

Apply the spec's constraints + the platform module's skip patterns. Common skips:

- Promotional posts (from members selling something).
- Off-topic posts (memes, irrelevant news).
- Posts older than 24 hours unless they have fresh activity (new comments today).
- Posts already answered by the user (don't reply to your own threads).
- Sensitive topics flagged in the spec's safety rules.

## Output

Report to the user in chat:

```
{{COMMUNITY_NAME}} — scan complete

Total posts scanned: <N>
Items identified:
- <K1> unanswered questions
- <K2> posts needing founder presence
- <K3> new member intros
- <K4> wins to celebrate

Skipped: <S> (promotional + off-topic + older than 24h)

Moving to Step 3 — drafting replies.
```

## On completion

Move to Step 3 — draft replies.
