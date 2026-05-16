# Step 1 — Open the community feed (read-only)

## What this step does

Open the community URL from the spec file in Claude in Chrome. **Read-only mode** — no write actions allowed for the entire run.

## Inputs

- Spec file: `projects/community-engagement/<slug>.md` (role must be `lead-scout`)
- `community_name`, `platform`, `url` from spec frontmatter

## Actions

1. Tell the user (in chat): "Opening `<community_name>` (`<platform>`) for lead scan at `<url>`. Read-only mode — no posts, no DMs, no engagement."
2. Use Claude in Chrome to navigate to `<url>`. **Confirm browser tool is in read-only / no-write mode before navigating.**
3. Wait for the page to render.
4. Confirm in chat: "Feed loaded. Found `<N>` recent posts visible. Moving to lead scan."

## The no-write check

Before any other action, the skill MUST verify Claude for Chrome cannot write to this community in this run:

- If Chrome tool is in "always allow writes" mode → HALT with: "Halt: Chrome tool is in 'always allow' mode. Lead-scan requires read-only. Switch Chrome to 'needs approval' or 'no writes' before this skill can run."
- If the platform module specifies any write paths → ensure all are disabled.

## Failure modes

- **Login required** → Halt: "Halt: not logged in to `<platform>`. Log in manually, say 'retry' here."
- **Page blocked** → Halt: "Halt: page says `<error>`. Check community membership / access."
- **Timeout** → Halt: "Halt: page didn't load in 30 seconds. Try again."

## On success

Move to Step 2 — scan for leads.
