# Phase 2 — Browser setup check

## Ask

For each community in `state-community.md`, run a one-time browser test.

For each community:

1. Tell the user: "I'm going to open `<community-name>` in a new Chrome tab. Watch the page load."
2. Use Claude in Chrome to navigate to the community's URL.
3. Wait for the page to render.
4. Ask: "Did the feed load? Pick one: yes / no, login required / no, blocked / no, other"

If **yes**: mark the community's `browser_check_status: ok` in state. Move on.

If **login required**: tell the user to log in manually in that tab. Wait. Re-test. If still failing after the user confirms login, escalate (skill cannot proceed for this community).

If **blocked**: ask: "What did the page say? (Forbidden / private / requires invite / something else?)" Log the error in state. Continue to next community but flag this one as `browser_check_status: failed` — the user can re-run the wizard for this community after fixing.

If **other**: ask for a description. Log. Flag as failed.

## Write

Update each community in `state-community.md`:

```yaml
communities:
  - slug: "<slug>"
    browser_check_status: "ok | login_required | failed"
    browser_check_notes: "<one-line note if failed>"
```

If at least one community passed, continue to Phase 3. If all communities failed, halt and tell the user to fix the browser/login situations first.

## Next

Move to Phase 3 — voice pull. Tell the user: "Browser checks done. <N> communities passed. Next I'll read your `writing-rules.md` and `business-brain.md` to bake your voice into every spec."
