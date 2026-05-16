# Platform module — Reddit

Loaded when a community has `platform: reddit` in state.

## What Reddit is

Reddit is the lead-scout gold mine. Subreddits in any niche have constant ICP pain-point posts. Strict no-promo rules make founder mode rare — most subreddits ban self-promo without explicit moderator permission. The agent works best here in lead-scout mode.

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Flairs to skip.**
   "List flairs to skip. Common: NSFW, off-topic, mod-announce, meta, weekly-thread. Add any subreddit-specific ones."
2. **External-link tolerance.**
   "How does this subreddit feel about external links? Strict / lenient / mixed. (Strict = the agent never includes external links even if I added them. Mixed = it can include them if a comment is asking.) For lead-scout, this doesn't matter — the agent never posts."
3. **Karma threshold.**
   "Skip posts from users with karma under what threshold? Default: 100. Filters out throwaway / spam accounts."

## Behaviors the agent should default to

- **Reading top comments too.** A Reddit post's value is often in the comments. The agent reads the post + top 3–5 comments before scoring it as a lead.
- **Sentiment matters.** A post complaining about a problem is a stronger lead than a post just describing one. The agent should rate emotional posts higher.
- **Username protection.** Reddit usernames are pseudonymous. The agent logs the username for the lead but does NOT include any PII attempts to identify the poster.
- **No DM signal abuse.** Some posts say "DM me." For lead-scout, the agent still doesn't DM — it surfaces the lead and the user decides. Cold DMs on Reddit are touchy.
- **Self-promo Saturday / weekly threads.** Many subreddits have weekly self-promo threads. Skip them by default — they're competitors, not leads.

## Skip patterns (lead-scout mode)

- Skip flairs listed in the wizard answer.
- Skip posts under the karma threshold.
- Skip stickied / mod-pinned posts (rules, announcements).
- Skip weekly recurring threads (self-promo Saturday, etc.).
- Skip posts marked [Removed] or [Deleted].
- Skip image-only posts unless the title is itself a clear ask.

## Founder-mode caveat

If the user is genuinely running a subreddit and wants founder-mode engagement, the spec needs explicit moderator permission flags and a much tighter constraint set. v0.1 supports it via the founder template + the `platform: reddit` notes block, but most subreddits have rules that conflict with daily AI-assisted posting. Manual moderation usually wins. Recommend reading r/modhelp first.

## Platform notes block (insert into spec file)

```markdown
- **Skipped flairs:** {{LIST_OF_FLAIRS}}.
- **Karma threshold:** posts from users under {{N}} karma are skipped.
- **Top-comment reading.** Score factors in top 3–5 comments, not just the post body.
- **Sentiment weighting.** Emotional / frustrated posts get +1 to the score.
- **Username:** logged for lead tracking, no PII attempts.
- **Self-promo threads:** skipped by default.
```
