# Step 2 — Scan for ICP-matching posts

## What this step does

Read the feed. Find posts from the last 24 hours that match the user's ICP pain phrases OR contain recommendation-request phrases.

## Inputs

- Spec file's pain phrases list (3+ phrases)
- Spec file's recommendation-request phrases list
- `about-me/business-brain.md` (ICP one-liner + full pain list for context)
- Last run's timestamp from `memory.md`

## What to match against

For each post in the last 24 hours, check:

1. **Pain phrase match.** Does the post body or title contain any of the spec's pain phrases (case-insensitive, with reasonable variants)?
2. **Recommendation-request match.** Does the post contain phrases like:
   - "looking for someone who…"
   - "any recs for…"
   - "who do you use for…"
   - "can anyone help with…"
   - "trying to find…"
   - (Plus any spec-specific additions)
3. **ICP context match.** Even if no specific phrase matches, does the post describe the user's ICP situation (using the ICP one-liner from `business-brain.md` as the reference)?

A post is a lead candidate if it matches ANY of the three.

## What to also pull for context

For each match, also capture:

- **Top 3–5 comments** on the post (high-engagement comments often clarify what the poster actually needs).
- **Poster's username / display name** (no PII attempts beyond what's publicly visible).
- **Post timestamp.**
- **Post URL / permalink.**
- **Any platform-specific signals** (Reddit karma, Skool level, FB profile picture presence, LinkedIn job title).

## Skip patterns

Apply the spec's skip patterns + platform module's skip patterns. Common skips:

- Posts older than 24 hours unless they have new comments today.
- Posts with platform-specific flags listed in skip patterns.
- Promotional posts (they're competitors, not leads).
- Reposts of the user's own content.
- Posts already pulled into prior `outputs/leads/` files in the past 7 days (dedupe).

## Output

Report to the user in chat:

```
{{COMMUNITY_NAME}} — scan complete

Total posts scanned: <N>
Pain-phrase matches: <P>
Recommendation-request matches: <R>
ICP-context matches: <I>

Total lead candidates: <C> (deduped vs the past 7 days)

Skipped: <S> (promotional + off-topic + platform-specific filters)

Moving to Step 3 — scoring.
```

## On completion

Move to Step 3 — score each lead 1–5.
