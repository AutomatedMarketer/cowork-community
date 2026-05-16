# cowork-community — architecture

## Purpose

A platform-agnostic, daily community engagement + lead-scout engine. Logs into the user's communities via Claude in Chrome, drafts replies and posts in the user's voice, or scans member-communities for leads. Plan-then-approve on every action. Soft-depends on `cowork-ai-os` for identity files.

## Skills overview

| Skill | Mode | Posts? | Reads | Writes |
|---|---|---|---|---|
| `/onboard-community` | wizard | no | `about-me/*`, prior `state-community.md` | per-community specs, schedule, `memory.md` |
| `/community-check <slug>` | founder | yes (after approval) | per-community spec, feed via Chrome | drafts in chat, posts after approval, `memory.md` |
| `/lead-scan <slug>` | lead-scout | NEVER | per-community spec, feed via Chrome | `outputs/leads/YYYY-MM-DD.md`, `memory.md` |
| `/community-grade` | grader | no | past 7d of `memory.md`, all specs | edits to specs, `memory.md` |
| `/community-engine-review` | retro | no | past 30d of `memory.md`, all specs | review note, recommendations, `memory.md` |

## File layout in user's Cowork workspace

```
Claude Cowork/
├── about-me/                                (cowork-ai-os fills this)
│   ├── about-me.md
│   ├── business-brain.md
│   ├── writing-rules.md
│   └── memory.md
├── projects/
│   └── community-engagement/
│       ├── state-community.md               (wizard resume state)
│       ├── <slug-1>.md                      (per-community spec)
│       ├── <slug-2>.md
│       └── memory.md                        (daily run log)
└── outputs/
    └── leads/
        └── YYYY-MM-DD.md                    (from /lead-scan)
```

## Three foundations (non-negotiable)

1. **Lazy-load context.** Each phase / step file is read only when the wizard or skill enters that phase / step. Never load the whole plugin upfront. Keeps daily runs fast and cheap.
2. **Self-improving skills.** Every run appends one line to `projects/community-engagement/memory.md` — what was generated, what was approved, what was edited, what was skipped. `/community-grade` reads this log weekly. The wizard re-reads it on re-runs.
3. **⚡ NEXT MOVE actionable close.** Every skill output ends with a `Next move:` block — Subject + Verb + Timing + Why. No skill ever ends with "let me know if you need anything." Always: "Post the 3 approved drafts now. Edit the Tuesday post to add the workshop link. Re-run at 9am tomorrow."

## Plan-then-approve — three layers

| Layer | Where | Says |
|---|---|---|
| 1. Handbook | `~/Claude Cowork/claude.md` | "Never auto-post anywhere." |
| 2. Skill spec | `projects/community-engagement/<slug>.md` safety section | "Approval gate. No post without explicit yes." |
| 3. Chrome tool | Claude for Chrome permissions | "Writes need approval. Always." |

A single approval bypass requires the user to actively disable all three. No accidental cascading.

## Browser path — Claude in Chrome

The plugin uses the Claude for Chrome extension (installed and signed in once by the user). Skills navigate via natural-language instructions — `"Open <URL>"`, `"Scroll down to load older posts"`, `"Click on the first unanswered question"`. No browser-automation scripting. The user's existing browser session is the auth gateway.

If Chrome is not available, the skill halts with an install link. v0.1 supports Chromium-based browsers (Chrome, Brave with extension installed). Firefox/Safari is on the v0.2 roadmap.

## Soft-dependency on cowork-ai-os

The wizard halts if:
- `about-me/about-me.md` is missing or empty
- `about-me/business-brain.md` is missing or empty
- `about-me/writing-rules.md` is missing or empty

Each halt redirects to the appropriate cowork-ai-os onboarding step. Never re-asks what cowork-ai-os already collected.

## Platform-agnostic design

Each community's spec file declares its `platform:` in frontmatter. Skills load the right platform module from `skills/onboard-community/platforms/<platform>.md` to ask the right questions and tune the right behaviors.

Out of the box: skool, facebook, circle, discord, slack, linkedin, reddit, mighty, generic.

Adding a new platform = adding a new file in `platforms/`. No skill code changes.

## Self-improvement loop

After every daily run, the skill appends one line to `memory.md`:

```
2026-05-16 09:00 /community-check my-skool — 5 drafts, 4 approved, 1 edited (too long), 0 skipped. Voice: on.
```

After 7 days, `/community-grade` reads these lines and edits the spec file based on patterns:

- If the same edit keeps coming up ("too long"), the grader tightens the reply length rule in the spec.
- If the agent keeps drafting replies the user skips, the grader adds the skip pattern to constraints.
- If the voice is consistently off in one direction, the grader updates the spec's voice section.

The user can always edit the spec by hand. The grader proposes — the user approves.
