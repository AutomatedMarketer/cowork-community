# Review report template

The output format for a monthly `/community-engine-review` run. Wider scope than `/community-grade` — looks across all communities for cross-cutting patterns and bigger structural changes.

```markdown
# /community-engine-review — {{YYYY-MM}}

Read the past 30 days of `projects/community-engagement/memory.md` across all communities + all `outputs/leads/` files for the month.

## Communities at-a-glance

| Slug | Role | Runs | Drafts/Leads | Approved % | Voice on | Status |
|---|---|---|---|---|---|---|
| {{SLUG_1}} | founder | {{N}} | {{N}} | {{PCT}}% | {{N/30}} days | {{HEALTHY/DRIFTING/CUT_CANDIDATE}} |
| {{SLUG_2}} | lead-scout | {{N}} | {{N}} (leads scored 3+) | n/a | n/a | {{HEALTHY/CUT_CANDIDATE}} |
| ... | ... | ... | ... | ... | ... | ... |

## Trend lines

**Approval-rate trend (founder communities):**
- Week 1: {{PCT}}%
- Week 2: {{PCT}}%
- Week 3: {{PCT}}%
- Week 4: {{PCT}}%

**Lead-quality trend (lead-scout communities):**
- Week 1: avg score {{X}}, top scores {{Y5}} (5s) / {{Y4}} (4s)
- Week 2: ...
- Week 3: ...
- Week 4: ...

**Time invested:** avg {{MIN}} min/day total across all communities.

## Cross-cutting recommendations

### Recommendation 1: {{HEADLINE}}
- **What:** {{ONE_LINE}}
- **Why:** {{REASON_FROM_PATTERN}}
- **How:** {{SPECIFIC_ACTION}}
- **Approve? (yes / discuss / skip)**

### Recommendation 2: {{HEADLINE}}
(repeat)

### Recommendation 3: {{HEADLINE}}
(repeat)

## Suggested cuts and adds

**Cut candidates (low ROI in the past 30 days):**
- {{SLUG}}: {{REASON}}. Removing frees {{MIN}}/week.

**Add candidates (ICP signals suggest these platforms not in your stack):**
- {{PLATFORM}}: {{REASON_FROM_LEADS_FILE_PATTERNS}}. Add via `/onboard-community`.

## Voice / business drift check

- `writing-rules.md` last edited: {{DATE}}
- `business-brain.md` last edited: {{DATE}}
- Drift detected: {{NONE / MINOR / MAJOR}}

If MAJOR: "Your voice or business has changed. Specs may be stale. Run `/onboard-community` Phase 3 to re-pull voice + business into the affected specs."

## Highlights of the month

- {{BEST_REPLY — quote a draft + post URL where the user said 'this nailed it'}}
- {{BEST_LEAD — top-scored lead that converted to a real conversation, if user logged it}}
- {{BEST_RUN — the day that felt smoothest}}

## ⚡ Next move

{{NEXT_MOVE_BLOCK — usually one of: "Approve the top 3 recommendations and re-run review next month" / "Run /onboard-community for the suggested add" / "Cut the underperforming community"}}

```

## Per-recommendation interaction

For each recommendation, render the block then **pause and wait for the user's answer**. Approved recommendations get a concrete follow-up scheduled or executed. "Discuss" loops back with the user for clarification before applying.

## Rendering rules

- Trends matter more than absolute numbers — always show week-over-week.
- Cuts come BEFORE adds. Pruning is usually higher-ROI than adding more.
- Voice / business drift check is critical — most plugin output decay traces back to drift in the source files.
- Highlights matter — surfaces what the user should keep doing, not just what to change.
