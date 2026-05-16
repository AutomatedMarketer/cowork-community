# Step 5 — Summarize in chat + suggest top DMs

## What this step does

Print a chat-ready summary so the user doesn't have to open the leads file unless they want depth. Surface the top 1–3 leads with one-line context each.

## The summary format

```markdown
## {{COMMUNITY_NAME}} — lead scan complete

**Today's leads:** {{TOTAL_3PLUS}} (score 3+) of {{TOTAL_SCANNED}} posts scanned.

**Score distribution:**
- Score 5: {{N5}}
- Score 4: {{N4}}
- Score 3: {{N3}}
- Flagged for human review: {{N_FLAGGED}}

**Top {{1_TO_3}} leads worth DMing today:**

1. **{{POSTER_NAME}}** (score {{SCORE}}) — {{ONE_LINE_CONTEXT}}.
   → Suggested opener: "{{ONE_SENTENCE_OPENER}}"
   → Link: {{POST_URL}}

2. **{{POSTER_NAME}}** (score {{SCORE}}) — {{ONE_LINE_CONTEXT}}.
   → Suggested opener: "{{ONE_SENTENCE_OPENER}}"
   → Link: {{POST_URL}}

3. (etc.)

**Full file:** `outputs/leads/{{DATE}}.md`

```

## Suggested opener rules

For each top lead, draft ONE sentence the user could send as a DM opener. Rules:

- **No pitches.** Never "I help X do Y, want to chat?"
- **Reference the specific post.** "Saw your post about <specific situation>" feels human.
- **Offer real value first.** "I've worked through this exact thing — happy to share what worked" or "Have you tried <specific approach>? Worked for a client with the same pattern."
- **End with a low-stakes ask.** "Open to a 10-minute call?" or "Want me to send the framework?"
- **Match the platform's tone.** Discord = short. LinkedIn = professional. Reddit = no link without earning it.

The user can use the opener as-is or edit it. The agent never sends the DM.

## When N_FLAGGED > 0

Surface the flagged leads at the bottom of the summary:

```markdown
⚠️ Flagged for human review (NOT included in suggested DMs):

- {{POSTER}} — {{REASON_FOR_FLAG}}
- {{POSTER}} — {{REASON_FOR_FLAG}}

```

## Render Next move + Self-improvement close

Use `templates/next-move-block.md` to render the actionable close (usually: "DM the top lead in the next hour"). Use `templates/self-improvement-close.md` to ask the 10% question.

## Append to memory.md

```
<ISO timestamp> /lead-scan <slug> — <total_scored_3plus> leads (5: <N5>, 4: <N4>, 3: <N3>), top suggested DM: <poster_name>.
```

## On completion

Exit the skill.
