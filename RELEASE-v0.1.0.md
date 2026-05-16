# Release Notes — v0.1.0 (2026-05-15)

## Summary

Initial public release of `cowork-community`. The final Wave 2 add-on plugin in the Cowork AI OS family. Daily community engagement + lead-scout engine. Platform-agnostic, browser-based, plan-then-approve.

## What's in v0.1.0

### Five skills

| Skill | Purpose |
|---|---|
| `/onboard-community` | 6-phase wizard. Multi-community, multi-platform. ≤15 min for one community, ~18 min for four. |
| `/community-check <slug>` | Founder mode. Drafts replies + 1 strategic post per day. Plan-then-approve. Never auto-posts. |
| `/lead-scan <slug>` | Lead-scout mode. Pulls leads scored 1–5 from communities the user is a member of. Read-only. Never posts. |
| `/community-grade` | Weekly grader. Reads past 7 days of `memory.md`, proposes spec edits to lock in what's working. |
| `/community-engine-review` | Monthly retro. Cross-community patterns, cut/add recommendations, voice/business drift check. |

### Platforms supported (out of the box)

Skool, Facebook Groups, Circle, Discord, Slack, LinkedIn Groups, Reddit, Mighty Networks, plus a generic "other" path for any browser-loadable community.

Adding a new platform = adding one file in `skills/onboard-community/platforms/`. No skill code changes.

### Browser path

Claude in Chrome. The user's already-logged-in browser. No session-persistence wiring. Works on Mac + Windows + Linux wherever Chromium-based browsers run.

### Three plugin foundations applied

1. **Lazy-load context.** Phase/step files read only when entered.
2. **Self-improving skills.** Every run appends one feedback line to `memory.md`. Friday `/community-grade` re-reads.
3. **⚡ NEXT MOVE actionable close.** Every output ends with Subject + Verb + Timing + Why.

### Plan-then-approve — three layers

1. Handbook (`~/Claude Cowork/claude.md`) says never auto-post.
2. Per-community spec safety section says approval gate.
3. Claude for Chrome tool stays on "needs approval" for writes.

`/community-check` re-checks all three at run time. `/lead-scan` enforces "no writes" at Step 1.

## Test results

20/20 GREEN. See `RELEASE-v0.1.0-TEST-REPORT.md`.

## Install

### Marketplace (recommended)

```
/plugin marketplace add automatedmarketer/cowork-community
/plugin install cowork-community@cowork-community
```

### Prerequisites

- `cowork-ai-os` installed and `/onboard` complete
- Claude for Chrome extension installed and signed in
- At least one community where you can log in via Chrome

## Course Project 07

Plugin is the build target of course Project 07 — Community Engagement. 6 SOP lessons walk through the install + daily rhythm + per-platform tips + maintenance.

## Not in v0.1

- DMs / private messages (feed only). Deferred to v0.2.
- Multi-account on a single platform.
- Cross-community analytics ("which platform brings best leads").
- Firefox / Safari (Chromium engines only).

## Known limitations

- Generic platform module relies on visual heuristics — may need spec tweaks for less-common platforms.
- Scheduled task creation depends on the user's task system; manual instructions surface if auto-create fails.
- Live tests are pending (require user to run on real Skool + FB Group). Static + inspection tests are 20/20.

## Related plugins

- [cowork-ai-os](https://github.com/AutomatedMarketer/cowork-ai-os) — foundation
- [cowork-obsidian](https://github.com/AutomatedMarketer/cowork-obsidian) — long-term memory
- [cowork-sales](https://github.com/AutomatedMarketer/cowork-sales) — daily sales ritual
- [cowork-research](https://github.com/AutomatedMarketer/cowork-research) — research engine
- [cowork-social](https://github.com/AutomatedMarketer/cowork-social) — social media content engine
- **cowork-community** ← shipped today
- cowork-financial (planned)
- cowork-highlevel (planned)
