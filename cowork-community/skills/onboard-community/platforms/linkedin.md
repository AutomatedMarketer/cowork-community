# Platform module — LinkedIn Groups

Loaded when a community has `platform: linkedin` in state.

## What LinkedIn Groups are

LinkedIn Groups are mostly low-activity now (LinkedIn deprioritized them years ago). They still work for lead-scout in B2B niches — small professional groups where decision-makers actually post questions. Founder mode is rare since active LinkedIn Groups are unusual.

For LinkedIn FEED comments and posts (outside groups), see `cowork-social` — that's a different plugin.

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Admin or member?**
   "Are you the admin / owner of this group, or a regular member? (Mostly relevant for moderation visibility.)"
2. **Frequency expectation.**
   "How active is this group? Default: low. The agent will produce 0–2 drafts most days, not 5–10."
3. **Member-log opt-in (lead-scout).**
   "When you find a high-scoring lead, should I log the LinkedIn profile URL for follow-up tracking? Default: yes — makes manual outreach easier."

## Behaviors the agent should default to

- **Professional register.** LinkedIn tone is more formal than FB, less formal than email. Avoid emoji except 1 max per post. No "great question!" — but also no jargon hedging.
- **Long-form is normal.** LinkedIn replies of 4–6 sentences are fine. The platform attracts longer-form thinking.
- **Profile context matters.** When drafting a reply, the agent should glance at the poster's title / company if available — tailor the reply to their level.
- **No external links without context.** LinkedIn shadow-bans external links sometimes. Default: no links in replies unless the post explicitly asks for one.

## Skip patterns (lead-scout mode)

- Skip group-admin announcements (rules, welcome posts).
- Skip "promoted" content (sponsored from outside the group).
- Skip posts from low-credibility profiles (no headline, no company, 100 connections).
- Skip events / job postings unless explicitly scoping for hiring leads.

## Platform notes block (insert into spec file)

```markdown
- **Admin vs member context.** {{ADMIN_OR_MEMBER}}.
- **Activity level.** Low. Expect 0–2 useful items per daily run.
- **Reply tone.** Professional. 4–6 sentences fine. Max 1 emoji.
- **Profile-context awareness.** Glance at title / company before drafting.
- **External links:** avoid unless the post requests one.
- **Lead profile logging:** {{ON_OR_OFF}} for follow-up tracking.
```
