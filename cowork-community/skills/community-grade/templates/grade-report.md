# Grade report template

The output format for a weekly `/community-grade` run. Shows the past-7-day analysis + proposed spec edits.

```markdown
# /community-grade — week ending {{YYYY-MM-DD}}

Read the past 7 days of `projects/community-engagement/memory.md`. Surfaced patterns. Proposed spec edits for each community.

## Communities reviewed

{{LIST_OF_SLUGS_WITH_RUN_COUNTS}}

---

## Per-community grade

### {{SLUG_1}} ({{ROLE}})

**Runs this week:** {{N_RUNS}}
**Total drafts/leads:** {{N_OUTPUTS}}
**Approval rate (founder mode):** {{APPROVED_PCT}}% approved as-is, {{EDITED_PCT}}% edited, {{SKIPPED_PCT}}% skipped
**Voice rating distribution (founder mode):** {{ON}}/{{OFF}}/{{MIXED}} days
**Average approval time:** {{MIN}} minutes

**Patterns surfaced:**
- {{PATTERN_1 — e.g. "Replies edited 4/7 days for being 'too long'"}}
- {{PATTERN_2 — e.g. "Monday post type 'repurpose YouTube' got skipped 2x (no recent video to repurpose from)"}}
- {{PATTERN_3 — e.g. "Funnel touch #2 used 4x — overweighted vs the others"}}

**Proposed spec edits:**

#### Edit 1
- **File:** `projects/community-engagement/{{SLUG}}.md`
- **Section:** Steps to execute → Step 3 (Reply rules)
- **Diff:**
  - Remove: `2–4 short paragraphs`
  - Add: `2–3 short paragraphs`
- **Reason:** "Too long" was the most common edit reason (4/7 days). Tightening default reduces edit rate.
- **Approve this edit? (yes / edit / skip)**

#### Edit 2
- **File:** `projects/community-engagement/{{SLUG}}.md`
- **Section:** Steps to execute → Step 4 (Rotation: Monday)
- **Diff:**
  - Remove: `Monday: Repurpose latest YouTube video`
  - Add: `Monday: Repurpose latest YouTube video OR quick tip from existing SOP if no recent video`
- **Reason:** "No recent video" was the skip reason 2x. Fallback prevents zero-post Mondays.
- **Approve this edit? (yes / edit / skip)**

---

### {{SLUG_2}} ({{ROLE}})

(repeat the same structure)

---

## Summary

**Edits proposed:** {{TOTAL_EDITS}}
**Edits approved:** {{APPROVED_AT_END}}
**Edits deferred:** {{DEFERRED}}

**Overall trend (this week vs last week):**
- Approval rate: {{LAST_WEEK_PCT}}% → {{THIS_WEEK_PCT}}% ({{DELTA}})
- Voice consistency: {{LAST_WEEK_VOICE_ON}}/{{THIS_WEEK_VOICE_ON}} days

## ⚡ Next move

{{NEXT_MOVE_BLOCK}}

```

## Per-edit interaction

For each proposed edit, render the edit block then **pause and wait for the user's answer**. Apply approved edits to the spec file. Log deferred edits with their reasons.

## Rendering rules

- Show ALL communities even if some had no edits proposed — surfaces healthy ones too.
- Always show the trend line — current week vs prior week. Patterns only matter as deltas.
- Next move at the end. Usually one of: "Run another calibration week" / "Switch to monthly review cadence" / "Re-onboard community X — too many skips suggest the spec is wrong, not the voice."
