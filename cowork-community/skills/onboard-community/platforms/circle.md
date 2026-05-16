# Platform module — Circle

Loaded when a community has `platform: circle` in state.

## What Circle is

Circle is a paid community platform with sub-communities called "spaces." Each space has its own feed. Members can be in some spaces but not others. Common for mid-sized paid communities ($30–$300/month).

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Spaces to watch.**
   "Which spaces should the agent watch? List 2–4 space names. The agent watches all of them but only posts in the one you designate as primary in the next question."
2. **Primary post space.**
   "Which space is the primary one for {{USER_NAME}}'s daily strategic post? (Default: the main / general space.)"
3. **Member directory.**
   "Can the agent read the member directory for context when drafting replies? (e.g. to check what someone's role is.) Default: yes — it improves reply relevance."

## Behaviors the agent should default to

- **Space discipline.** The daily post goes in ONE space only (the primary). Cross-posting feels spammy on Circle.
- **Cross-space replies are fine.** The agent should reply to questions in whatever space they were asked — that's what spaces are for.
- **DMs are out of scope** in v0.1 — even though Circle has them.
- **@-mentions** in Circle notify; use them only when replying directly to someone.

## Skip patterns (lead-scout mode)

Rare — Circle is mostly paid, so lead-scout there is unusual. If used:

- Skip onboarding / welcome / "say hi" threads.
- Skip community-meta posts ("what should we add to the platform?").
- Skip event RSVPs.

## Platform notes block (insert into spec file)

```markdown
- **Watched spaces:** {{LIST_OF_SPACES}}.
- **Primary post space:** {{PRIMARY_SPACE}} — daily strategic post goes here only.
- **Cross-space replies:** allowed. Reply where the question was asked.
- **DMs:** out of scope in v0.1.
- **Member directory:** {{ALLOWED_OR_NOT}} for context.
```
