# Platform module — Slack

Loaded when a community has `platform: slack` in state.

## What Slack is

Slack is a chat-style platform used for both client workspaces (founder mode — paying clients only) and public Slack communities (lead-scout mode — niche professional groups like Mind the Product, Demand Curve, RevGenius). Pace is fast like Discord, but tone is more business-formal.

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Channels on-topic.**
   "Which channels are on-topic for the agent? List the names (without the #). Skip private channels the agent shouldn't read."
2. **Workspace type.**
   "Is this a client workspace (paying customers) or a community workspace (members)? Default: ask, then customize tone accordingly."
3. **DMs.**
   "Should DMs be in scope? Default: NO in v0.1. DMs in client Slacks are usually account-management work that should go through the user, not the agent."

## Behaviors the agent should default to

- **Reply length.** Slack tone is shorter. 1–3 sentences feel right. 4+ sentence replies feel off. Long detailed replies belong in threads, not the main channel.
- **Threads are heavily used.** Reply in the thread if one exists. Start a thread only if the reply is substantive (3+ sentences) and would clutter the channel otherwise.
- **Mentions notify.** @username pings the user. Use sparingly — only when answering a direct question.
- **Reactions are first-class.** A 👀 / 👍 / 🙏 reaction can be the right reply on its own. Especially for "thanks!" or "got it" messages where a written reply is overkill.
- **Status awareness.** Slack shows when someone is "away" — don't tag away members for non-urgent replies.

## Skip patterns (lead-scout mode)

For big public Slacks:

- Skip channels named #intros, #welcome, #general (signal-to-noise too low unless explicitly checking for new members).
- Skip "self-promo" channels — those are competitors, not leads.
- Skip job-board channels unless lead-scout is specifically scoping for hiring leads.
- Skip threads under posts older than 48 hours (slow-burn for Slack).

## Platform notes block (insert into spec file)

```markdown
- **Watched channels:** {{LIST_OF_CHANNELS}} (without the #).
- **Workspace type:** {{CLIENT_OR_COMMUNITY}}. Tone: {{TONE_RULE}}.
- **Reply length:** 1–3 sentences in channel. Longer goes in thread.
- **Threads:** {{REPLY_IN_THREAD_OR_NEW}}.
- **Reactions allowed.** A 👀 / 👍 / 🙏 reaction can replace a written reply.
- **DMs:** out of scope in v0.1.
```
