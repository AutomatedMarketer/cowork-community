# Phase 0 — Welcome and prereq check

## Ask

Welcome the user. State the goal in one sentence:

> "I'm going to set up your daily community engagement engine. You'll add one or more communities — your own Skool / FB Group / Circle / Discord (founder mode) and/or any communities you're a member of where you want to scout for leads (lead-scout mode). I'll generate one spec file per community, schedule daily runs, and walk you through the first run. About 12 minutes for one community, ~18 for four."

Then run prereq checks in this order:

1. **cowork-ai-os identity files.** Read `about-me/about-me.md`, `about-me/business-brain.md`, `about-me/writing-rules.md`. If any is missing or empty, halt with:
   > "Missing: `<file>`. Run `/onboard` from cowork-ai-os first. I'll be here when you finish."
2. **Claude for Chrome.** Ask: "Do you have the Claude for Chrome extension installed and signed in?" If unsure, give the install link and pause.
3. **State file.** Check for `projects/community-engagement/state-community.md`. If it exists, ask: "I see a prior wizard run. Resume where you left off, or start fresh?" If start fresh, archive the old state file to `state-community-archive-<timestamp>.md`.

Run the validation rubrics in `checks/identity-files-present.md` and `checks/chrome-extension-present.md`. Halt and surface the specific fix if either fails.

## Write

If all checks pass, create `projects/community-engagement/state-community.md` with:

```yaml
---
current_phase: 1
started_at: <ISO timestamp>
last_updated: <ISO timestamp>
communities: []
---
```

## Next

Move to Phase 1 — communities. Tell the user: "Prereqs look good. Next I'll ask you to list the communities you want to add. You can add 1 to N. We'll go one at a time."
