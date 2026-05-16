# Step 3 — Draft replies in user's voice

## What this step does

For every item identified in Step 2, draft a reply in the user's voice using the spec + `writing-rules.md` as the voice source.

## Inputs

- Items identified in Step 2 (with full post content + author level / role)
- Spec file's voice section (pocket reference)
- `about-me/writing-rules.md` (full voice book — only loaded when a draft feels uncertain)
- Spec's constraints section (what topics to avoid, banned phrases, etc.)

## Drafting rules

For each item, follow the priority-specific rules:

### Unanswered questions
- Direct, no fluff. Say the thing in sentence 1.
- Practitioner-first — speak from experience. Not "research suggests…" but "I've done this with clients…"
- 2–4 short paragraphs.
- End 50%+ with a follow-up question to keep the thread alive.
- Apply funnel touches per Step 5 (max 1 per reply, only when relevant).

### Founder presence (team replied, user didn't)
- Briefly acknowledge the team's answer ("Building on what `<team-member>` said…" or similar).
- Add the founder's unique angle — usually a deeper context, a personal anecdote, or a sharper opinion.
- 1–3 paragraphs. Shorter than question replies.
- No funnel touches here — feels weird.

### New member welcomes
- 1–2 short sentences. Warm but not effusive. No "Welcome to the community!!!!"
- Reference something specific from their intro post (name, where they're from, what they're working on).
- End with one specific suggestion ("Check out the `#getting-started` channel" or "Tag someone if you want to be introduced.")
- No funnel touches.

### Wins / milestones
- Celebrate specifically. "Nice work hitting X" not "Awesome!"
- Push to next step naturally. "What's the next thing on your list?" or "Have you tried Y to compound this?"
- 1–2 sentences.
- Funnel touches OK if they fit (e.g. "This is exactly what we cover in the workshop next week" if the win is workshop-relevant).

## Voice check

Before showing each draft, do a quick internal voice check:

- Does this sound like sample writing in `writing-rules.md`? Yes / no / not sure.
- If "not sure," flag it for the user with: "Not 100% sure this matches your voice — read carefully?"
- If "no," rewrite once. If still "no," skip the draft and surface why.

## Banned phrases (apply automatically)

Scan every draft for the kill list from `writing-rules.md`. Common banned openers:
- "Great question!"
- "Absolutely!"
- "Certainly!"
- "I'd be happy to help"
- "In today's fast-paced world"
- "Let's dive into"
- "It's worth noting that"

If any of these appear, regenerate the sentence.

## Output

For each draft, generate a block using `templates/reply-block.md`. Render all drafts in chat. Move to Step 4 before asking for approval — drafts + post are reviewed together at Step 6.

## On completion

Move to Step 4 — draft the strategic post.
