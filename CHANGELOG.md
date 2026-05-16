# Changelog

All notable changes to `cowork-community` are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.1.0] — 2026-05-15

### Added

- Initial public release. Five skills shipped.
- `/onboard-community` — 6-phase wizard. Multi-community, multi-platform aware. Reads `business-brain.md` + `writing-rules.md` to bake voice into specs.
- `/community-check <slug>` — Founder mode. Drafts replies + 1 strategic post per day. Plan-then-approve, never auto-posts.
- `/lead-scan <slug>` — Lead-scout mode. Pulls leads from communities the user is a member of. Writes to `outputs/leads/YYYY-MM-DD.md`. Never posts.
- `/community-grade` — Weekly grader. Reviews voice consistency and approval-gate adherence, edits per-community specs based on the past week's patterns.
- `/community-engine-review` — Monthly retro. Surfaces cross-community patterns and recommends spec changes.
- Platform support out of the box: Skool, Facebook Groups, Circle, Discord, Slack, LinkedIn Groups, Reddit, Mighty Networks, and a generic "other" path for any browser-loadable community.
- Three plugin foundations applied: lazy-load context, self-improving skills (one feedback line per run), `⚡ NEXT MOVE` actionable close on every output.
- Per-community spec template at `_templates/sample-files/community-agent-sample.md` (in the course composition workspace) with new YAML frontmatter block — community_name, platform, url, role, schedule, voice/business sources.

### Browser path

- Uses Claude in Chrome (the user's already-logged-in browser). No session-persistence wiring needed. Cross-platform — works on Mac + Windows + Linux wherever Chrome runs.

### Not in v0.1

- DMs / private messages. Feed engagement only. Deferred to v0.2.
- Multi-account on a single platform (e.g. switching FB accounts mid-run).
- Cross-community analytics ("which platform brings best leads"). Manual for now.
- Native MCP integrations beyond Claude-in-Chrome.
- Firefox / Safari support. Chromium engines only (Brave often works because the extension installs).
