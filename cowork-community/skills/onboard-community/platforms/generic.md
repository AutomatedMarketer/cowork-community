# Platform module — Generic / Other

Loaded when a community has `platform: other` in state. This is the fallback for any web-based community not covered by the dedicated platform modules.

## What this covers

Anything browser-loadable that has a feed of member posts and a way to comment / reply. Examples: niche forum software, custom-built community apps, smaller platforms (Heartbeat, Bettermode, Hivebrite, Disciple, Tribe), self-hosted Discourse / phpBB / NodeBB instances.

## Platform-specific wizard questions (Phase 4)

Ask these in addition to the role-specific questions:

1. **Platform name.**
   "What's the platform name (just for my notes)? Example: 'Heartbeat', 'self-hosted Discourse', 'custom community app'."
2. **Feed location.**
   "Where on the page is the feed of new posts? Top of page / sidebar / main column / I'm not sure (the agent will scroll and look)."
3. **Sub-communities.**
   "Are there sub-communities / spaces / channels? If yes, list 2–4. If no, the agent treats the main feed as the only target."
4. **Admin vs member.**
   "Are you admin / mod / regular member?"
5. **Browser test result.**
   (Already captured in Phase 2 — re-confirm if anything was iffy.)

## Behaviors the agent should default to

- **Generic web-page reader mode.** The agent treats the community like a styled webpage. It reads visible text, identifies post boundaries by visual cues (avatars, timestamps), and extracts the content.
- **Slower scroll.** Without platform-specific scroll APIs, the agent scrolls in 500-pixel increments and waits for content to load before scanning.
- **Conservative on actions.** Without platform-specific button identifiers, the agent should describe what it sees and confirm with the user before clicking anything in founder mode.
- **Skip dynamic UI.** Floating modals, popovers, "subscribe to our newsletter" overlays — the agent dismisses them before scanning.

## Skip patterns (any mode)

- Skip whatever the user explicitly told the wizard to skip.
- Skip cookie banners and consent dialogs (auto-dismiss when possible).
- Skip "you're not signed in" pages (halt and tell the user to log in).
- Skip pages that require an action the user didn't approve (e.g. "verify your email first").

## Platform notes block (insert into spec file)

```markdown
- **Platform:** {{PLATFORM_NAME}} (treated as generic web).
- **Feed location:** {{LOCATION_ON_PAGE}}.
- **Sub-communities:** {{LIST_OR_NONE}}.
- **Conservative actions.** Agent confirms before clicking unfamiliar buttons in founder mode.
- **Scroll behavior:** 500px increments, waits for content to load.
- **Skip on encounter:** cookie banners, consent dialogs, non-signed-in pages.
```

## When the user reports "agent can't read the feed"

Common fixes in order:

1. **Confirm logged in.** Most generic platforms hide the feed behind auth.
2. **Confirm correct URL.** Some platforms have different URLs for "feed" vs "home" vs "dashboard."
3. **Browser cache.** Sometimes a hard refresh fixes a stale render.
4. **Tell the agent more.** Edit the spec's `feed_location` note to be more specific — e.g. "the feed is the second section under the navbar, after the 'Welcome' banner."
5. **Escalate to v0.2.** If a platform consistently fails the generic reader, the user can request a dedicated platform module for v0.2.
