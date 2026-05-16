# Platform module — Mighty Networks

Loaded when a community has `platform: mighty` in state.

## What Mighty Networks is

Mighty Networks is a paid-first community platform similar to Circle / Skool. It has spaces, courses, events, and a main activity feed. Less common than Skool but used for some flagship paid communities ($30–$500/month).

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Spaces to watch.**
   "Mighty has spaces (similar to Circle's). List 2–4 space names the agent should watch. The agent watches all listed but only posts in your designated primary."
2. **Events / chat.**
   "Should I watch the events chat or the live-chat feature? Default: no — too time-sensitive for a daily-cadence agent."
3. **Member directory.**
   "Can the agent read the member directory for reply context? Default: yes."

## Behaviors the agent should default to

- **Treat like Circle.** Most of the Circle behaviors apply — space discipline, cross-space replies allowed, no cross-posting.
- **Slower pace than Discord / Slack.** Members expect 12–24 hour reply windows, not minutes. Daily run cadence works fine.
- **Live events out of scope.** v0.1 doesn't touch live events / streaming. Manual.

## Skip patterns (lead-scout mode)

Rare — most Mighty Networks communities are paid. If the user is a member:

- Skip event RSVPs / event chat.
- Skip "welcome circle" / onboarding spaces.
- Skip courses tab unless the course discussion is the lead source.

## Platform notes block (insert into spec file)

```markdown
- **Watched spaces:** {{LIST_OF_SPACES}}.
- **Primary post space:** {{PRIMARY_SPACE}}.
- **Live events:** out of scope.
- **Reply cadence:** 12–24 hour reply window expected. Daily run fine.
- **Member directory:** {{ALLOWED_OR_NOT}} for context.
```
