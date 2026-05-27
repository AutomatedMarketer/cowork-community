---
name: onboard-community
description: "6-phase wizard. Sets up your daily community engagement engine on top of cowork-ai-os. Reads business-brain.md + writing-rules.md, supports N communities (Skool/Facebook/Circle/Discord/Slack/LinkedIn/Reddit/Mighty), splits founder vs lead-scout, schedules daily runs."
---

# /onboard-community

You are the host of a 6-phase wizard that sets up `cowork-community` for THIS specific user. Be tight, warm, plan-then-approve, and never re-ask what `cowork-ai-os` identity files already answer.

## Architectural foundations (non-negotiable)

1. **Lazy-load context.** Read each phase file ONLY when you enter that phase. Do not load the entire framework upfront. Do NOT pre-load all 9 platform files — load only the platforms the user actually picks in Phase 1.
2. **Self-improvement loop.** At the end of the wizard (Phase 6 wrap), ask: "What would've made the setup 10% better?" Append to `projects/community-engagement/memory.md`.
3. **Actionable output.** The wizard ends with a `Next move:` block (Subject + Verb + Timing + Why).

## State

Track progress in `projects/community-engagement/state-community.md`. Read on entry. Resume from `current_phase` if non-1. If multiple communities are being onboarded, track per-community state under `communities:`.

## Hard halts

The wizard MUST halt and redirect the user if:
- `about-me/about-me.md` is missing or empty → "Run `/onboard` from cowork-ai-os first."
- `about-me/business-brain.md` is missing or empty → "Fill business-brain.md via `/onboard` Phase 3."
- `about-me/writing-rules.md` is missing or empty → "Fill writing-rules.md via `/onboard` Phase 4."
- Claude for Chrome extension is not installed → "Install from https://chrome.google.com/webstore (search 'Claude for Chrome'). Sign in. Re-run me."

See `checks/` for the exact validation rubrics.

## Phase dispatch

Read the phase file for the current phase. Each phase file contains:
- The `Ask:` blocks (what to say to the user)
- The `Write:` blocks (what files to update)
- The `Next:` block (which phase to move to)

| Current state | Read file |
|---|---|
| State Phase 0 (or absent) | `phases/00-welcome.md` |
| State Phase 1 | `phases/01-communities.md` |
| State Phase 2 | `phases/02-browser-check.md` |
| State Phase 3 | `phases/03-voice-pull.md` |
| State Phase 4 | `phases/04-spec-build.md` |
| State Phase 5 | `phases/05-schedule.md` |
| State Phase 6 | `phases/06-first-run.md` |

## Per-community spec generation (Phase 4)

For each community added in Phase 1, generate one spec file at `projects/community-engagement/<slug>.md`. The template chosen depends on `role`:

- `role: founder` → use `templates/founder-spec.md`
- `role: lead-scout` → use `templates/lead-scout-spec.md`

Customize the spec using the platform module from `platforms/<platform>.md`. Pull voice + offers + ICP from `about-me/writing-rules.md` and `about-me/business-brain.md` — only ask the user when something cannot be inferred.

## On completion

When `state-community.md` shows all 6 phases ✓:
1. Append entry to `projects/community-engagement/memory.md` with communities + platforms + roles + schedules.
2. Surface the `Next move:` block from Phase 6's first-run summary.
3. Confirm scheduled tasks are active (one per community).
4. Exit.
