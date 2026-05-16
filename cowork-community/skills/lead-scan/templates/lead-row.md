# Lead row template

Use this format for each scored lead (3+) appended to today's leads file.

```markdown
### {{POSTER_NAME}} — score {{SCORE}} {{HUMAN_REVIEW_FLAG_IF_APPLICABLE}}

**Posted:** {{POST_TIMESTAMP — local time + relative}} (e.g. "2026-05-16 08:24 UTC · 4 hours ago")
**Link:** {{POST_URL}}
**Platform context:** {{PLATFORM_SPECIFIC_INFO}}

**Quoted snippet:**
> {{EXACT_QUOTE_FROM_POST — first 300 chars max, with ellipsis if truncated}}

**Why this is a lead:** {{ONE_LINE_REASONING}}

**Suggested next move:** {{ACTION}}

---

```

## Field rules

### `{{POSTER_NAME}}`
- Use the display name visible on the platform (e.g. Reddit username, Facebook first name + last initial, LinkedIn full name).
- Never include email, phone, or any data not visible on the public post.

### `{{SCORE}}`
- Integer 3, 4, or 5. Anything below 3 is skipped (not written).

### `{{HUMAN_REVIEW_FLAG_IF_APPLICABLE}}`
- Empty if no flag.
- `⚠️ HUMAN_REVIEW` with a one-line reason if the lead should be vetted before outreach.

### `{{POST_TIMESTAMP}}`
- ISO local time + relative time. Format: `YYYY-MM-DD HH:mm <tz> · N hours ago`.

### `{{POST_URL}}`
- The direct link to the post / thread. Never a profile URL.

### `{{PLATFORM_SPECIFIC_INFO}}`
- Reddit: karma count, subreddit, post flair.
- Skool: member level, courses-completed.
- Facebook: admin / member, profile-picture presence.
- LinkedIn: title + company (visible publicly).
- Discord/Slack: server role, message count visible.
- Other: whatever's visible.

### `{{EXACT_QUOTE_FROM_POST}}`
- Verbatim. No paraphrasing.
- 300 chars max. Truncate with `...` if longer.
- Use blockquote syntax (`>`) for visual separation.

### `{{ONE_LINE_REASONING}}`
- Why does this match the user's ICP / qualify as a lead?
- Specific: "Asks for marketing consultant + mentions $5k budget + is a SaaS founder (matches ICP exactly)."
- Not generic: not "Could be a good fit." 

### `{{ACTION}}`
- One of: `Manual DM with this opener` / `Public comment first then DM` / `Wait — watching for more comments` / `Skip — flagged for human review`.

## Examples

### Score 5 with DM suggestion

```markdown
### Sarah K. — score 5

**Posted:** 2026-05-16 14:32 UTC · 2 hours ago
**Link:** https://reddit.com/r/SaaS/comments/abc123/
**Platform context:** Reddit · 12k karma · SaaS subreddit · "founder" flair

**Quoted snippet:**
> Just hit $40k MRR with my B2B tool but my Asana is a complete mess. Lost 6 hours yesterday hunting for one decision the team made 3 weeks ago. Looking for someone who's helped a small team (we're 7 people) set up a real operations system. Budget around $3-5k for the engagement. DM me.

**Why this is a lead:** Direct ask for ops consulting + $40k MRR (matches ICP) + budget signal + decision-maker.

**Suggested next move:** Manual DM with this opener.

---
```

### Score 4 without explicit budget

```markdown
### MarkP — score 4

**Posted:** 2026-05-16 11:15 UTC · 5 hours ago
**Link:** https://facebook.com/groups/saascommunity/posts/...
**Platform context:** Facebook · admin badge · profile pic present

**Quoted snippet:**
> Anyone else struggle to keep their team docs organized? We have 9 people across 3 timezones and Notion just feels like a graveyard at this point. Tried Coda, tried Confluence, nothing sticks.

**Why this is a lead:** Specific ops pain (matches "team docs disorganized" in business-brain.md) + team size matches ICP. No budget signal yet — would warrant a public comment first, then DM.

**Suggested next move:** Public comment first then DM.

---
```

### Flagged for review

```markdown
### lonely_dev_24 — score 4 ⚠️ HUMAN_REVIEW

**Posted:** 2026-05-16 03:47 UTC · 13 hours ago
**Link:** https://reddit.com/r/depression/...
**Platform context:** Reddit · 245 karma · r/depression · "venting" flair

**Quoted snippet:**
> My startup failed and I've been spiraling for weeks. Can't focus on building anything. Everyone says "get help" but I can't even open Calendly to book a therapist.

**Why this is a lead:** ICP context match (failed startup founder) but the post is about mental health.

**Suggested next move:** Skip — flagged for human review. This is not a cold-outreach situation. Nuno can decide if a personal reach-out is appropriate based on existing relationship.

---
```
