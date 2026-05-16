# Step 4 — Draft ONE strategic post for today

## What this step does

Generate one original post for today, based on the 7-day rotation in the spec.

## Inputs

- Spec file's 7-day rotation block (`{{MONDAY_POST_TYPE}}`, `{{TUESDAY_POST_TYPE}}`, etc.)
- Today's day-of-week
- The user's `about-me/business-brain.md` (for offers + content references)
- Recent run history from `memory.md` (so the agent doesn't repeat the same post type / angle from last week)

## The rule

ONE post per day. Not zero, not two. The 7-day rotation tells the agent which TYPE today's post should be. The agent generates ONE concrete post matching that type.

If the rotation says "Sunday: OFF / no post" → skip the post entirely. Tell the user: "Today is Sunday — no post per the rotation."

## Post-type-specific guidance

| Rotation type | What to do |
|---|---|
| Repurpose a YouTube video | Clip from the latest video. 2–4 sentences. CTA to watch the full thing. Include the video URL. |
| Engagement question | Ask something the user's ICP will argue about in the comments. Make it specific, not generic. |
| Quick tip | One concrete thing they can try today. Pull from existing SOPs / videos. Cite the source. |
| Promote upcoming event | Workshop / office hours / live stream / new product. Date + time + what they'll get + how to join. |
| Resource drop | Link to a YouTube video, SOP, or template. 1–2 sentence pitch + the link. |
| Poll or hot take | Something that drives comments. "X is dead — agree or disagree?" |
| Off / no post | Skip entirely. Don't draft anything. |

## Voice check

Same voice rules as Step 3 — apply `writing-rules.md` standards, scan for banned phrases, voice-check before showing.

## Funnel touch in the post (different rule than replies)

Posts CAN include a funnel touch in a more explicit way than replies. The post IS the founder showing up — it's expected to be promotional in spirit if not in word. Default touch placement:

- Repurpose post → CTA to watch the full video (the touch is natural).
- Promote event → the entire post is a touch.
- Engagement question / quick tip / poll → no touch usually, unless the answer naturally references an offer.
- Resource drop → the resource link itself is the touch.

## Output

Generate the post using `templates/post-block.md`. Add to the draft list rendered in chat. The user will approve all replies + this post together at Step 6.

## On completion

Move to Step 5 — funnel touches.
