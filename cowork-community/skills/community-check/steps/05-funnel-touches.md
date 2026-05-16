# Step 5 — Weave funnel touches into replies

## What this step does

For each reply drafted in Step 3, decide if it gets a funnel touch and which one. Max 1 per reply. Only when natural.

## Inputs

- Drafts from Step 3 (replies only — posts handled their own touches in Step 4)
- Spec file's `Funnel touches` section — 3 pre-written touch lines
- The original post content (what the member asked / wrote)

## The rule

A funnel touch fits naturally if:

- The post is about a problem the user's offer solves.
- The post asks for a resource (the user has one).
- The post is a win the user can credibly say "this is what we do" to.

A funnel touch DOES NOT fit if:

- The post is about a different topic entirely.
- The funnel touch would feel like a pitch / out of left field.
- The reply is already 4 paragraphs long (touch makes it 5 — too long).
- The poster explicitly said "no DMs / no offers please."

## Selection logic

For each reply, score each of the 3 touches for fit (1–5). If the top score is 4+, weave that touch in. If the top score is 3 or below, no touch.

## How to weave

Touches should feel like a natural extension of the reply, not a tacked-on PS. Examples:

❌ Bad: "Hope that helps! PS we cover this in VIP office hours."
✅ Good: "We dig into this exact pattern in VIP office hours — happy to share the framework if useful."

❌ Bad: "Great point! BTW the workshop covers this."
✅ Good: "This is the kind of thing the upcoming workshop is built around — same situation, three founders working through it together."

The touch should reference the post's specific situation, not just plug the offer.

## Track usage

After each touch is woven in, increment a counter so the same touch isn't used 5x in one daily run. Cap: each touch used max 2x per run. After 2x usage of a touch, skip remaining replies' touches even if they'd otherwise fit.

## Output

Update the drafts in chat — re-render each reply with the touch woven in (where applicable). Show the user: "Touches woven in: <N>/{{TOTAL_REPLIES}} replies."

## On completion

Move to Step 6 — approval gate.
