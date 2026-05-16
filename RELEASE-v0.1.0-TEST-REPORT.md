# v0.1.0 Test Report — 2026-05-15

## Summary

- **Tests passing:** 20/20
- **Static checks run:** 5 (Tests 1, 13, 16, 19, 25)
- **Inspection checks:** 15
- **Final verdict:** GREEN — clear to tag v0.1.0 + push release.

---

## Test results

| # | Test | Type | Result | Notes |
|---|---|---|---|---|
| 1 | plugin.json valid JSON | Static | PASS | `python -c "import json; json.load(open('.claude-plugin/plugin.json'))"` returns clean. name=cowork-community, version=0.1.0, author={name, url} present. |
| 2 | Wizard golden path | Inspection | PASS | All 7 phase files present (00-welcome through 06-first-run). Phase dispatch table in `onboard-community/SKILL.md` maps every phase to its file. State tracked in `projects/community-engagement/state-community.md`. |
| 3 | Halt on missing identity files | Inspection | PASS | `checks/identity-files-present.md` defines exact halt rules for `about-me.md`, `business-brain.md`, `writing-rules.md`. Lead-scout mode requires 3+ pain phrases. Empty-file rule documented. `phases/00-welcome.md` runs the check before any Ask block. |
| 4 | Halt on missing Chrome extension | Inspection | PASS | `checks/chrome-extension-present.md` defines install link + browser test. Skip-allowed path documented for dry-run installs. |
| 5 | Per-community spec generation | Inspection | PASS | 2 spec templates present (`templates/founder-spec.md`, `templates/lead-scout-spec.md`). Both have YAML frontmatter block (community_name, platform, url, role, schedule, voice_source, business_source, last_updated). Phase 4 dispatch logic chooses the right template based on role. |
| 6 | Founder vs lead-scout skill separation | Inspection | PASS | `community-check/SKILL.md` hard-halts if spec role is not `founder`. `lead-scan/SKILL.md` hard-halts if spec role is not `lead-scout`. The two skills never run on the wrong spec. |
| 7 | `/lead-scan` never-write rule | Inspection | PASS | `lead-scan/SKILL.md` documents "no-write rule (never bypass)" section. `lead-scan/steps/01-open-feed.md` halts the run if Chrome tool is in "always allow writes" mode. The browser tool stays read-only for the entire run. |
| 8 | `/community-check` three-layer approval gate | Inspection | PASS | `community-check/SKILL.md` documents the three layers (handbook + spec + Chrome tool). `community-check/steps/06-approval-gate.md` re-checks all three at run time. Halts if any layer is bypassable. |
| 9 | Lazy-load discipline | Inspection | PASS | All 5 SKILL.md files have an explicit "Architectural foundations — Lazy-load context" section. Each step/phase file is read only when entered. Platform modules are loaded only for the platforms users actually pick. |
| 10 | Self-improvement loop wired everywhere | Inspection | PASS | All 5 skills append to `projects/community-engagement/memory.md`. Each skill has its own `self-improvement-close.md` template (community-check + lead-scan) or equivalent inline (onboard + grade + review). Append format is specified per skill. |
| 11 | Actionable next-move close | Static + Inspection | PASS | `⚡ NEXT MOVE` / `⚡ Next move` block present at every output point: community-check (`next-move-block.md`), lead-scan (`next-move-block.md`), onboard-community (`phases/06-first-run.md`), community-grade (`grade-report.md`), community-engine-review (`review-report.md`). Subject + Verb + Timing + Why structure enforced. |
| 12 | Platform-agnostic — 9 platform modules | Inspection | PASS | 9 platform modules present: skool, facebook, circle, discord, slack, linkedin, reddit, mighty, generic. Each follows the same structure (Platform-specific wizard questions / Behaviors / Skip patterns / Notes block to insert into spec). Adding a new platform = adding a new file. |
| 13 | No guru names in plugin output | Static (grep) | PASS | `grep -ri -l -E "(julie\|chenell\|brunson\|hormozi\|belcher\|dotcom secrets\|expert secrets\|acquisition\.com\|\$100M offers\|\$100M leads\|funnel hacking\|war room\|russell\|perry\|alex hormozi)" cowork-community/skills/` — ZERO matches. |
| 14 | Voice pull from writing-rules + business-brain | Inspection | PASS | `phases/03-voice-pull.md` reads both files, surfaces tone / banned phrases / ICP / pains for confirmation, updates state with the pulled values. Phase 4 spec-build uses the pulled values. |
| 15 | Banned-phrase enforcement | Inspection | PASS | `community-check/steps/03-draft-replies.md` has a "Banned phrases (apply automatically)" section listing common AI-tell phrases. Every draft is scanned before showing to the user. |
| 16 | README has all expected sections | Static | PASS | README contains: 5 skills table, install (Marketplace UI + slash command), prerequisites (cowork-ai-os + Chrome ext), the two modes (founder + lead-scout with full step lists), three foundations, three approval-gate layers, course Project 07 reference, related plugins, license. |
| 17 | Lead-row format includes safety + score + suggested action | Inspection | PASS | `lead-scan/templates/lead-row.md` requires: poster name, score 3+, human-review flag if applicable, post URL, platform context, exact quoted snippet, why-this-is-a-lead one-line, suggested-next-move (one of 4 actions). No PII beyond publicly visible. |
| 18 | Reply-block format includes voice rating + approval | Inspection | PASS | `community-check/templates/reply-block.md` requires: original post quote, where it posts, proposed reply, length stats, funnel-touch flag, agent's voice self-rating, approval prompt. |
| 19 | Spec frontmatter on community-agent-sample.md (course workspace template) | Static | PASS | `Claude Co-Work/_templates/sample-files/community-agent-sample.md` updated with YAML frontmatter block (community_name, platform, url, role, schedule, voice_source, business_source, last_updated). Lead-scout addendum added at bottom. |
| 20 | `/community-grade` weekly + `/community-engine-review` monthly cadence | Inspection | PASS | grade-report.md template includes per-edit approval flow. review-report.md template includes cross-cutting recs with cut/add candidates + voice/business drift check. Both surface trends week-over-week / month-over-month. |

---

## Cross-test verification — the 3 plugin foundations

| Foundation | Implementing files | Confirmed |
|---|---|---|
| **Lazy-load context** | All 5 SKILL.md + every phase/step file | Test 9 |
| **Self-improvement skills** | All 5 skills append to `memory.md`; close templates exist | Test 10 |
| **⚡ NEXT MOVE actionable close** | 5 output points carry the canonical block | Test 11 |

All 3 foundations green.

---

## Plugin shape — final count

- **Files in plugin:** 48 (1 plugin.json + 1 architecture.md + 5 SKILL.md + 7 onboard phases + 2 checks + 9 platforms + 2 spec templates + 6 community-check steps + 4 community-check templates + 5 lead-scan steps + 4 lead-scan templates + 1 grade report template + 1 review report template)
- **Skills:** 5 (`/onboard-community`, `/community-check`, `/lead-scan`, `/community-grade`, `/community-engine-review`)
- **Platforms supported out of the box:** 9
- **Browser path:** Claude in Chrome (cross-platform)

---

## Live-Cowork tests pending (non-blocking for GitHub push)

These require Nuno to run them in a clean Cowork session post-install to confirm runtime behavior matches the static design:

| Test | How Nuno runs it live |
|---|---|
| Wizard live | `/onboard-community` on a fresh setup with his real Skool + 1+ FB Groups → confirm wall time ≤18 min for 2–4 communities + state file complete |
| Founder-mode live | `/community-check <skool-slug>` → confirm Chrome opens, feed reads, drafts appear, approval gate holds, approved posts go live |
| Lead-scout live | `/lead-scan <fb-group-slug>` → confirm Chrome opens read-only, leads file lands at `outputs/leads/YYYY-MM-DD.md`, no posts/DMs occur |
| Approval-gate stress test | Try to force a post without saying "yes" → must be impossible across all 3 layers |
| Banned-phrase enforcement live | Plant a banned phrase in a draft → must be auto-rewritten |
| 7-day calibration | Run for 7 days → `/community-grade` proposes spec edits based on patterns |

---

## Conclusion

- **Static + inspection: 20/20 PASS**
- Dynamic in-Cowork verification: procedure documented above
- **Recommendation: GO for v0.1.0 tag + GitHub release**
