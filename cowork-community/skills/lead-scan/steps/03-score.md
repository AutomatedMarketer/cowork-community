# Step 3 — Score each lead 1–5 for fit

## What this step does

For every lead candidate from Step 2, assign a fit score. Surface only scores 3+. Skip 1–2 (log them but don't include in the daily file).

## The rubric

| Score | Means | Example |
|---|---|---|
| **5** | Direct ask for what the user offers + budget signal + appears to be a decision-maker | "Looking to hire a marketing consultant — budget around $5k/month. Just need someone who's done D2C SaaS before. DM me." |
| **4** | Strong ICP pain match + explicit ask for help | "Spent 6 hours today on Asana and still can't figure out the workflow. Anyone got a better system?" |
| **3** | ICP pain match but no explicit ask | "I keep falling off my content schedule. Doesn't matter what app I use." |
| **2** | Tangential mention of pain | "Marketing is hard." |
| **1** | Weak signal — just a topic mention | "Anyone else use Asana?" |

## What to factor in

For each candidate, weigh these factors:

1. **Pain specificity** — vague pain (2) vs specific pain with details (4+).
2. **Ask explicitness** — no ask (–1) vs implied ask (+0) vs explicit ask (+2).
3. **Budget signal** — none (0) vs hint at willingness to pay (+1) vs explicit budget (+2).
4. **Decision-maker signal** — unknown / IC (0) vs founder / decision-maker (+1).
5. **Recency** — older than 24h (-1) vs within last 24h (+0).
6. **Engagement** — 0 comments (–1) vs 5+ thoughtful comments showing the poster is engaged (+1).
7. **Emotional weight** (Reddit / FB specific) — neutral (0) vs frustrated / motivated (+1).

Cap at 5. Floor at 1.

## What to flag for human review

Even if the score is high, flag the lead with `⚠️ HUMAN_REVIEW` if:

- The post contains sensitive content (mental health, financial crisis, legal trouble) — the user handles those personally, not via cold outreach.
- The platform has strict no-promo / no-DM rules (some subreddits) — the user should comment publicly first, not DM.
- The poster's profile suggests they're a competitor or someone in the user's actual market who'd see a DM as weird.

Flagged leads still appear in the file but with the warning.

## Output

For each lead scored 3+, prepare the data for Step 4 (write to file). Print a one-line summary to chat:

```
{{COMMUNITY_NAME}} — scoring complete

Score 5: <N5> leads
Score 4: <N4> leads
Score 3: <N3> leads
Skipped (1–2): <S>
Flagged for human review: <F>

Total to surface in today's file: <TOTAL>

Moving to Step 4 — write leads file.
```

## On completion

Move to Step 4 — append to leads file.
