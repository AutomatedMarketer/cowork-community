# Cowork Community

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](./LICENSE)
[![Version](https://img.shields.io/badge/version-0.1.0-brightgreen.svg?style=flat-square)](./CHANGELOG.md)
[![Platform: Mac · Windows · Linux](https://img.shields.io/badge/platform-Mac%20%C2%B7%20Windows%20%C2%B7%20Linux-blue.svg?style=flat-square)](#install)
[![Built for Claude Cowork](https://img.shields.io/badge/built%20for-Claude%20Cowork-7C3AED.svg?style=flat-square)](https://claude.com/product/cowork)

**Your daily community engagement + lead-scout engine, attached to your Cowork AI OS.**

A [Claude Cowork](https://claude.com/product/cowork) plugin (also runs in [Claude Code](https://claude.com/product/claude-code)) that logs into your communities every weekday morning via Claude in Chrome, drafts replies in your voice, scans member-communities for leads, and waits for your approval before posting anything. Platform-agnostic — works with any browser-loadable community: Skool, Facebook Groups, Circle, Discord, Slack, LinkedIn Groups, Reddit, Mighty Networks, and more.

Built by [Nuno Tavares](https://nunomtavares.com) for community founders, course creators, coaches, and anyone who uses other people's communities as a lead source.

---

## The 5 skills

| Skill | What it does |
|---|---|
| `/onboard-community` | 6-phase wizard. Reads your `business-brain.md` + `writing-rules.md`, asks about each community (founder or lead-scout), customizes per platform, schedules the daily runs. ~12–18 minutes depending on how many communities you add. |
| `/community-check <slug>` | Founder mode. Opens your own community in Claude in Chrome. Drafts replies to unanswered questions + 1 strategic post per day. Every draft waits for your approval before going live. |
| `/lead-scan <slug>` | Lead-scout mode. Reads a community you're a member of. Scores posts 1–5 for ICP-fit. Writes a leads file to `outputs/leads/YYYY-MM-DD.md`. Never posts, never DMs. |
| `/community-grade` | Weekly grader. Reads the past week's `memory.md` entries. Tells you if the voice held, where edits clustered, and edits the per-community spec accordingly. |
| `/community-engine-review` | Monthly retro. Surfaces what's working and what to change across all your communities. |

---

## Install

### Option 1 — Marketplace UI (recommended)

1. Open Claude Cowork → click your name (top right) → **Customize**
2. Click **+Plugins** → **Add Marketplace**
3. Search for `automatedmarketer/cowork-community` → click **Install**

### Option 2 — Slash command

```
/plugin marketplace add automatedmarketer/cowork-community
/plugin install cowork-community@cowork-community
```

---

## Prerequisites

- **`cowork-ai-os` installed and onboarded.** This plugin reads your `about-me/` files. Run `/onboard` from `cowork-ai-os` first if you haven't.
- **Claude for Chrome extension installed.** Free, one-time install. The wizard checks for it and gives you the install link if it's missing.
- **At least one community where you can log in via Chrome.** Skool, Facebook Group, Circle, Discord, Slack, LinkedIn Group, Reddit, Mighty Networks, or any other web-based community works.

---

## The two modes

### Founder mode — `/community-check`

For communities **you run**. Built around daily presence.

1. Open your community in Claude in Chrome.
2. Scan the last 24 hours — unanswered questions, posts with team replies but no founder reply, new member intros, member wins.
3. Draft replies in your voice for every unanswered question.
4. Draft one strategic post from the 7-day rotation you set in the wizard.
5. Weave in funnel touches (your offers, content, affiliate links) where they fit naturally.
6. Show every draft. Wait for your approval. Post what you said yes to.

Reply rate target after the 7-day calibration: ~10% edits, ~90% one-click approvals.

### Lead-scout mode — `/lead-scan`

For communities **you're a member of**. Built around lead discovery.

1. Open the community in Claude in Chrome.
2. Scan the last 24 hours for posts that match your ICP pain phrases.
3. Score each match 1–5 for fit. Pull the quoted snippet, the link, and the poster's name.
4. Append everything to today's `outputs/leads/YYYY-MM-DD.md`.
5. Print a summary in chat: total leads, top 3 highest-scored, suggested DMs.

The agent never DMs. The agent never posts. You decide which leads to reach out to.

---

## The three foundations (non-negotiable)

Every skill in this plugin follows three rules:

- **Lazy-load context.** Each daily run reads only what it needs. No giant context dumps.
- **Self-improving skills.** Every run appends one feedback line to `projects/community-engagement/memory.md`. The wizard re-reads memory to calibrate.
- **⚡ NEXT MOVE actionable close.** Every run ends with a `Next move:` block — Subject + Verb + Timing + Why.

---

## Plan-then-approve — the three layers

This plugin will never post anything without you explicitly saying yes. Three layers protect against accidental posts:

1. **The handbook (`claude.md`)** says never auto-post, anywhere, ever.
2. **The skill spec** (`projects/community-engagement/<slug>.md`) lists the approval gate in its safety rules section.
3. **The Claude for Chrome tool** stays on "needs approval" for any write action.

If any one layer fails, the other two still hold. If all three fail at once, you have bigger problems than this plugin.

---

## Course Project 07

This plugin is the build target of **course Project 07 — Community Engagement** in the Claude Co-Work course. The 6 SOP lessons walk you through the install + the daily rhythm + per-platform tips + maintenance. See [the course index](https://github.com/AutomatedMarketer/cowork-ai-os) for context.

---

## Related plugins

This plugin is part of the **Cowork AI OS** family:

- [`cowork-ai-os`](https://github.com/AutomatedMarketer/cowork-ai-os) — foundation (identity files, daily brief, file org)
- [`cowork-obsidian`](https://github.com/AutomatedMarketer/cowork-obsidian) — long-term memory layer
- [`cowork-sales`](https://github.com/AutomatedMarketer/cowork-sales) — daily sales ritual
- [`cowork-research`](https://github.com/AutomatedMarketer/cowork-research) — research engine
- [`cowork-social`](https://github.com/AutomatedMarketer/cowork-social) — social media content engine
- **`cowork-community`** ← you are here
- `cowork-financial` (planned) — Mercury/Stripe/PayPal + monthly P&L
- `cowork-highlevel` (planned) — GoHighLevel CRM integration

Install one. Live with it. Add the next.

---

## License

[MIT](./LICENSE)
