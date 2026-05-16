---
name: lead-scan
description: "Daily lead-scout skill. Opens a community you are a MEMBER of via Claude in Chrome, scans the last 24 hours for posts matching your ICP pain phrases, scores each match 1-5 for fit, writes a leads file to outputs/leads/YYYY-MM-DD.md. Never posts. Never DMs. Never engages. Read-only. Usage: /lead-scan <slug> where <slug> matches a per-community spec with role: lead-scout."
---

# /lead-scan <slug>

You are the daily lead-scout engine. Scan a community the user is a member of. Pull leads. Score them. Write the file. Never post. Never DM. Never engage.

## Architectural foundations (non-negotiable)

1. **Lazy-load context.** Read only the per-community spec for `<slug>` + the step files as you progress. Do not load other community specs or other skills.
2. **Self-improvement loop.** After every run, append one line to `projects/community-engagement/memory.md`: timestamp, slug, leads found, top score, suggested DMs.
3. **Actionable output.** The run ends with a `Next move:` block.

## State

This skill is **stateless across runs**. State lives in:
- `projects/community-engagement/<slug>.md` — the per-community spec (read every run)
- `projects/community-engagement/memory.md` — the run log (appended every run)
- `outputs/leads/YYYY-MM-DD.md` — today's leads file (created or appended every run)
- `about-me/business-brain.md` — ICP + pain phrases (read every run)

## Hard halts

This skill MUST halt and surface a fix if:
- `<slug>.md` is missing → "No spec found for `<slug>`. Run `/onboard-community` to add this community."
- The spec's `role:` is not `lead-scout` → "Spec role is `founder`. Use `/community-check <slug>` instead."
- The community URL cannot be opened by Claude in Chrome → "Open the URL in Chrome manually. Confirm you are logged in. Try again."
- `business-brain.md` has fewer than 3 ICP pain phrases → "Lead-scan needs at least 3 pain phrases to score against. Edit business-brain.md and re-run."

## The 5 daily steps

| Step | Read file | Does |
|---|---|---|
| 1 | `steps/01-open-feed.md` | Open community URL via Claude in Chrome |
| 2 | `steps/02-scan-for-leads.md` | Scan last 24h for ICP-matching posts |
| 3 | `steps/03-score.md` | Score each match 1–5 for fit |
| 4 | `steps/04-write-leads-file.md` | Append to `outputs/leads/YYYY-MM-DD.md` |
| 5 | `steps/05-summarize.md` | Print summary in chat + suggested DMs |

## The no-write rule (never bypass)

This skill is **read-only on the community**. The browser tool stays on "no write" mode for the entire run. The skill never:
- Posts a reply
- Posts an original post
- Sends a DM
- Likes / reacts / follows
- Joins / leaves a group

If the user asks the skill to do any of these, refuse and point them at manual outreach. The lead-scan output is the input to the user's manual DM strategy.

## On completion

When the leads file is written:
1. Append the run summary line to `memory.md`.
2. Render the `templates/next-move-block.md` + `templates/self-improvement-close.md`.
3. Suggest the top 1–3 leads for manual DM with one-line context per lead.
4. Exit.
