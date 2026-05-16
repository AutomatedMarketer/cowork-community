# Step 1 — Open the community feed

## What this step does

Open the community URL from the spec file in Claude in Chrome. Confirm the feed is rendered and visible.

## Inputs

- Spec file: `projects/community-engagement/<slug>.md` (read once at run start)
- `community_name`, `platform`, `url` from spec frontmatter

## Actions

1. Tell the user (in chat): "Opening `<community_name>` (`<platform>`) at `<url>`."
2. Use Claude in Chrome to navigate to `<url>`.
3. Wait for the page to render. Watch for the feed selector matching the platform.
4. Confirm in chat: "Feed loaded. Found `<N>` recent posts visible. Moving to scan."

## Failure modes

- **Login required** — page rendered the login screen instead of the feed. Halt with: "Halt: looks like you're not logged in to `<platform>` in Chrome. Log in manually in that tab, then say 'retry' here."
- **Page blocked** — community is private or you don't have access. Halt with: "Halt: page says `<error>`. Check community access. Re-run when fixed."
- **Timeout** — page took longer than 30 seconds. Halt with: "Halt: page didn't load in 30 seconds. Try again, or check internet connection."

## On success

Move to Step 2 — scan.
