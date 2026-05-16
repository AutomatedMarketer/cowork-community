# Platform module — Discord

Loaded when a community has `platform: discord` in state.

## What Discord is

Discord is a real-time chat-style community platform with channels (topic-based), threads (sub-discussions), and voice channels. Pace is much faster than Skool / FB / Circle. Members expect replies within minutes-to-hours, not 24 hours later.

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Channels to watch.**
   "Which text channels should the agent watch? List the names (without the #). Skip voice channels — out of scope. Skip announcement / moderation channels."
2. **Threads behavior.**
   "How should I handle threads? Pick: read-and-reply / read-only / ignore. Default: read-and-reply (threads are where the real conversation happens)."
3. **Bot-assist role.**
   "Should the agent post as {{USER_NAME}}'s normal role, or under a separate 'bot-assist' role? Default: normal role. Members appreciate it being from you, not a labeled bot."

## Behaviors the agent should default to

- **Speed window.** Discord replies more than 30 minutes after a post feel weird. Schedule the daily run for when the user is genuinely available to approve quickly. Or use a "morning catch-up" framing — explicitly say "missed this last night, here's my take" if replying to overnight posts.
- **Thread vs channel.** Reply in the thread if the post started one. Reply in the channel if it didn't. Never start a new thread just to reply (clutters the channel list).
- **Reactions count.** Sometimes a thumbs-up emoji reaction is the right move instead of a full reply. The agent can suggest reactions in the draft preview — "I'd react with 👍 here instead of writing a reply" — and the user approves.
- **Code blocks.** Discord renders \`\`\`triple-backtick blocks for code. Use them when the reply includes code or a structured list.

## Skip patterns (lead-scout mode)

- Skip channels named announcements, rules, mod-only, or similar.
- Skip posts in voice-channel chat (those are noise).
- Skip messages from bots (look for the BOT tag next to the username).
- Skip messages that are reactions-only (someone just pasting an emoji).

## Platform notes block (insert into spec file)

```markdown
- **Watched channels:** {{LIST_OF_CHANNELS}} (without the #).
- **Threads:** {{READ_AND_REPLY_OR_OTHER}}.
- **Reply speed.** Posts >30 minutes old get a "missed this last night" preface.
- **Reactions allowed.** The agent can suggest a 👍 / ❤️ / 😂 reaction instead of a written reply when that's the right move.
- **Code blocks.** Use \`\`\`triple-backtick when replying with code or structured lists.
```
