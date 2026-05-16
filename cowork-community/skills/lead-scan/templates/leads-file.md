# Leads file template

The header that goes at the top of `outputs/leads/YYYY-MM-DD.md` when it's first created today.

```markdown
---
date: YYYY-MM-DD
generated_by: cowork-community v0.1
type: daily-leads
---

# Leads — YYYY-MM-DD

Daily leads from `/lead-scan` runs across all your scout communities. Sorted by score descending within each community.

**How to use this file:**

1. Read the top 1–3 in chat (the skill surfaces them automatically).
2. Open the full file if you want depth — score 4+ are worth a manual DM today.
3. Score 3 = worth watching but not chasing yet (post may evolve, more comments may clarify).
4. Flagged ⚠️ = read carefully before acting. Some leads are sensitive (mental health, financial crisis, legal trouble) — don't cold-pitch them.

**Safety reminder:** the agent never DMs. It surfaces. You decide. Every outbound message is yours.

---

```

After the header, each community's `/lead-scan` run appends its own `## {{COMMUNITY_NAME}}` section.

## When to use this template

- File doesn't exist yet today → create with this template + community section.
- File exists today → skip this template, append the new community section to the existing file.

## File hygiene

- One file per day. Never split / merge across days.
- Never overwrite. Always append.
- If a community runs twice in one day (unusual), append a new section with the second timestamp.
