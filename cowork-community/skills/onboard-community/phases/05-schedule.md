# Phase 5 — Schedule the daily runs

## Ask

For each community in state with `spec_status: ok`, ask:

1. **Time.** "Run `<community-name>` at what time? Default: weekday 9am for founder communities, weekday 11am for lead-scout. Or pick: <time>."
2. **Weekends.** "Weekends on or off? Default: off."
3. **Confirm.** "I'll create a scheduled task that runs `/community-check <slug>` (or `/lead-scan <slug>`) at <time> on <days>. Approve?"

Loop until all communities are scheduled.

## Create the scheduled task

For each approved schedule, create a scheduled task using the user's task system (Cowork's built-in scheduler or system cron). The task should:

- Run on the days the user picked (default: weekdays only)
- Fire at the time the user picked (default: 9am for founder, 11am for lead-scout)
- Execute `/community-check <slug>` (if `role: founder`) or `/lead-scan <slug>` (if `role: lead-scout`)
- Log to `projects/community-engagement/memory.md` on completion

## If scheduling fails

If the scheduled task cannot be created automatically (some platforms don't expose a task API), surface the manual instructions:

> "I couldn't create the scheduled task automatically on this system. To set it up manually: Open Claude Desktop → Settings → Scheduled Tasks → New Task. Name: `<community-name>`. Command: `/community-check <slug>` (or `/lead-scan <slug>`). Time: <time>. Days: <days>. Save."

## Write

Update each community in state:

```yaml
communities:
  - slug: "<slug>"
    schedule_status: "ok | manual_required"
    schedule_time: "09:00"
    schedule_days: "weekdays"
```

## Next

Move to Phase 6 — first run. Tell the user: "Schedules set. Last step: I'll run the first check on each community right now so you see how the approval flow works. Takes about 5 minutes per community."
