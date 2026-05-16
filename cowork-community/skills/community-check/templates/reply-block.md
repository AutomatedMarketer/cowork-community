# Reply block template

Use this format every time a reply draft is shown to the user. One block per draft. Numbered for easy reference.

```markdown
### Draft #{{N}} — Reply to {{POSTER_NAME}} ({{POSTER_LEVEL_OR_ROLE}})

**Original post** ({{POST_TIMESTAMP}}):
> {{ORIGINAL_POST_QUOTE — first 200 chars or full if shorter}}

**Where this posts:** {{THREAD_OR_CHANNEL_PATH}}

**Proposed reply:**

{{REPLY_BODY}}

**Length:** {{N}} sentences, {{N}} paragraphs.
**Funnel touch:** {{NONE | TOUCH_TEXT — touch #{{1|2|3}}}}
**Voice rating (my gut check):** {{ON | OFF | NOT_SURE}}

---

⏸ Approve? (yes / edit / skip — if edit, tell me the change)
```

## Rendering rules

- One draft per block — never bundle multiple drafts in one block.
- Always show the original post quote. Member needs context.
- Show "Where this posts" so the user knows the thread the reply attaches to.
- Length stats matter — surfaces "too long" before the user has to spot it.
- Voice rating is the agent's self-assessment, not the user's. Flagging "NOT_SURE" prompts the user to read carefully.
