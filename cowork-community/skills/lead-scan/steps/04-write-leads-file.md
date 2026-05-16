# Step 4 — Append to outputs/leads/YYYY-MM-DD.md

## What this step does

For each scored lead (score 3+), append a block to today's leads file. Multiple lead-scout communities can write to the same file — they append, never overwrite.

## File location

`outputs/leads/YYYY-MM-DD.md`

If the file doesn't exist yet today, create it with a header:

```markdown
---
date: YYYY-MM-DD
generated_by: cowork-community v0.1
---

# Leads — YYYY-MM-DD

```

Each community's `/lead-scan` run appends its block under this header.

## The community section format

For each community run, append a section:

```markdown
## {{COMMUNITY_NAME}} ({{PLATFORM}}) — <RUN_TIMESTAMP>

**Total leads:** <N> (Score 5: <N5> · Score 4: <N4> · Score 3: <N3>)
**Run duration:** <SECONDS>

```

Followed by one block per lead, using `templates/lead-row.md`. Highest-scored leads first.

## Per-lead block

Use the format from `templates/lead-row.md`:

```markdown
### {{POSTER_NAME}} — score {{SCORE}} {{HUMAN_REVIEW_FLAG_IF_APPLICABLE}}

**Posted:** {{POST_TIMESTAMP}}
**Link:** {{POST_URL}}
**Platform context:** {{PLATFORM_SPECIFIC_INFO — e.g. Reddit karma, Skool level, LinkedIn title}}

**Quoted snippet:**
> {{EXACT_QUOTE_FROM_POST — first 300 chars max}}

**Why this is a lead:** {{ONE_LINE_REASONING}}

**Suggested next move:** {{ONE_OF — Manual DM with this opener / Public comment first then DM / Wait — too early / Skip — flagged}}

```

## Safety rules

- **Never include PII beyond what's publicly visible.** No emails. No phone numbers. No attempts to look up the poster on other platforms.
- **Always include the original post URL.** Lets the user verify the context before reaching out.
- **No personal opinions about the poster.** Just observed facts and scoring rationale.

## Output

Confirm in chat:

```
✏️ Wrote {{N}} leads to outputs/leads/{{DATE}}.md
```

## On completion

Move to Step 5 — summarize for the user in chat.
