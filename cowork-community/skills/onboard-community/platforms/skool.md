# Platform module — Skool

Loaded when a community has `platform: skool` in state.

## What Skool is

Skool is a paid-first community platform with levels, courses (the "classroom" tab), and a main feed. Members earn levels by activity. Founders often run paid Skool groups as their primary community home.

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Level threshold for new-member welcome.**
   "Which levels count as 'new' for welcome posts? Default: levels 1–2."
2. **Classroom watching.**
   "Watch only the main feed, or also classroom comments? Default: main feed only — classroom comments add noise unless the agent should engage there."
3. **Daily pin.**
   "Pin your daily post to the top, or post it into the feed without pinning? Default: post without pinning (pinning is for high-impact announcements)."

## Behaviors the agent should default to

- **Skool levels work as identity.** When scanning, the agent should note each poster's level. Higher-level members get less effusive replies (they don't need hand-holding). Lower-level members get warmer welcomes.
- **"New" notification.** When a member levels up, Skool surfaces it in the feed. Agent should celebrate level-ups (founder mode) — short, sincere, no emoji-spam.
- **Tagging.** Skool tagging sends a notification. Use sparingly — only when directly answering a member's question.
- **Founder badge.** Members can tell when the founder replies vs a team member. The agent's voice matters more here than on most platforms.

## Skip patterns (lead-scout mode)

For Skool communities where the user is a member (rare — most Skools are paid):

- Skip course/classroom posts unless they're specifically asking for help.
- Skip leaderboard-only posts (just announcing levels).
- Skip Skool platform-level meta posts ("new feature in Skool…").

## Platform notes block (insert into spec file)

```markdown
- **Skool levels.** Members levels 1–2 get warmer welcomes. Levels 5+ get peer-to-peer replies.
- **Classroom comments.** {{INCLUDE_OR_NOT}}.
- **Tagging.** Use only when directly answering a tagged-in member's specific question.
- **Founder badge.** Members notice when {{USER_NAME}} replies personally — voice consistency matters more here than on FB.
```
