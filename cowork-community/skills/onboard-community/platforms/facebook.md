# Platform module — Facebook Groups

Loaded when a community has `platform: facebook` in state.

## What Facebook Groups are

Facebook Groups are the most common lead-scout target — big niche groups with hundreds of thousands of members where ICP pain phrases appear daily. Also viable as a free-community founder platform, though paid platforms (Skool, Circle) usually serve better.

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Admin or member?**
   "Are you admin / moderator of this group, or a regular member? (This affects what posts the agent can see — admins see hidden / pending posts, members don't.)"
2. **Promotional posts.**
   "How should I handle promotional posts? Default for founder: skip them (they're noise). Default for lead-scout: skip them (they're competitors, not leads)."
3. **Feed filter.**
   "Should I watch 'recent activity' or 'newest posts'? Default: newest posts."

## Behaviors the agent should default to

- **Notifications.** Admin replies notify members. Member replies don't (usually). Tone matters — stay warm, never lecture.
- **Comment depth.** FB Group threads can go 5+ levels deep. The agent should reply at the level it's most useful — usually directly under the original post, not buried in a sub-thread.
- **Promotional radar.** FB Groups have strict no-promo rules in most niches. The agent NEVER posts anything that could be flagged as promo unless the spec explicitly says so for a specific post type.
- **Tagging.** Use member name (e.g. "@John") when replying directly to someone — FB renders this as a notification. Use first name only — no full names.

## Skip patterns (lead-scout mode)

- Skip posts flagged "promotional" by the admin / mods.
- Skip posts that already have 50+ comments (signal is buried — your DM will be lost).
- Skip posts from users with no profile picture (often fake accounts).
- Skip posts older than 24 hours unless they have fresh activity (new comments today).

## Platform notes block (insert into spec file)

```markdown
- **Admin vs member context.** {{ADMIN_OR_MEMBER}}. Admin replies notify; member replies don't.
- **Promotional posts.** {{SKIP_OR_LOG}}.
- **Comment depth.** Reply directly under the original post unless joining an existing sub-thread.
- **Tagging.** Use first name only when tagging members for replies.
- **24-hour freshness window.** Posts older than 24h get skipped unless they have new comments today.
```
