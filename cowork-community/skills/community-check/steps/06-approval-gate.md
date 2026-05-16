# Step 6 — Show every draft, wait for approval, post approved ones

## What this step does

The approval gate. For each draft (replies + post), wait for the user to say one of: "post it" / "edit X" / "skip." Only post the ones the user explicitly approves.

## The flow

For each draft, ONE AT A TIME (not all at once):

1. **Show the draft** using the rendered `templates/reply-block.md` or `templates/post-block.md`. Include: the original post quote, the proposed reply, where it would post (which thread / channel), and any funnel touch flag.
2. **Ask:** "Post this? (yes / edit / skip) — if edit, tell me the change."
3. **Wait for the user's answer.** Do NOT proceed to the next draft until you hear from them.
4. **Apply the answer:**
   - **yes / approve / post it** → use Claude in Chrome to post the draft. Confirm in chat: "Posted." Note the post URL if visible.
   - **edit `<change>`** → apply the change to the draft. Re-show. Loop back to the ask.
   - **skip** → log the skip with reason (ask for reason if not given). Move to next draft.

## The three layers (re-check at run time)

Before posting ANYTHING, double-check all three layers:

1. **Handbook** — `~/Claude Cowork/claude.md` says never auto-post. Approval gate is the override.
2. **Spec safety** — the per-community spec's safety section requires approval.
3. **Chrome tool** — Claude for Chrome stays on "needs approval" for writes. Each post triggers an approval prompt.

If ANY layer would auto-skip the approval (e.g. user set Chrome to "always allow"), HALT the run and tell the user:

> "Halt: Claude for Chrome is on 'always allow' for writes. That bypasses the approval gate. Switch it back to 'needs approval' in Chrome settings before this skill can run."

This is a hard rule. No exceptions.

## After all drafts processed

Print a summary:

```
{{COMMUNITY_NAME}} — daily run complete

Drafts produced: {{TOTAL}}
- Approved as-is: {{APPROVED}}
- Edited and approved: {{EDITED}}
- Skipped: {{SKIPPED}}

Posts that went live: {{LIVE_COUNT}} (see URLs above)

Voice rating (your gut check): on / off / mixed?
```

Wait for the user's voice rating. Log it to `memory.md`.

## Append to memory.md

```
<ISO timestamp> /community-check <slug> — <total> drafts, <approved> approved, <edited> edited, <skipped> skipped. Voice: <on/off/mixed>. Time: <approval_minutes> min.
```

## Render Next move + Self-improvement close

Use `templates/next-move-block.md` to render the actionable close. Use `templates/self-improvement-close.md` to ask the 10% question.

## On completion

Exit the skill.
