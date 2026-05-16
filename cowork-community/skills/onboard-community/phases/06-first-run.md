# Phase 6 — First run + verification

## Ask

For each community in state, ask:

> "Ready to run the first check on `<community-name>`? Yes or skip. Skipping just means the first real run is tomorrow at <scheduled-time>."

For each "yes":

1. **Call the right skill.**
   - `role: founder` → invoke `/community-check <slug>` (the actual skill, with its full 6-step flow).
   - `role: lead-scout` → invoke `/lead-scan <slug>` (the actual skill, with its full 5-step flow).

2. **Watch the run together.** The wizard hands control to the child skill. The child skill runs its full daily flow, including the approval gate for founder mode.

3. **When the child skill exits**, ask: "How did that go? Voice on? Anything off?"

4. **Capture feedback** — append to `projects/community-engagement/memory.md`. Common feedback shapes:
   - "Voice was on" → mark this as a green run.
   - "Reply 2 was too long" → log; will surface in `/community-grade` next Friday.
   - "Skipped the Monday post — wrong topic" → log; may need to edit the rotation in the spec.

Loop until all communities have had a first run (or been skipped).

## The self-improvement loop close

After all first runs:

> "What would have made this setup 10% better? (One line is fine. I'll add it to memory so future wizards do this better for you and for anyone else who runs them.)"

Append to `projects/community-engagement/memory.md`:

```
<ISO timestamp> /onboard-community completed
  - Communities: <list of slugs>
  - First-run feedback: <user's 10% line>
```

## Write

Update state:

```yaml
current_phase: complete
completed_at: <ISO timestamp>
```

## Next: render the summary

Print a clean summary:

```
✅ cowork-community v0.1 installed

Communities:
- <slug-1> (<role>, scheduled for <time> <days>)
- <slug-2> (...)
- ...

What you'll see tomorrow at <earliest-time>:
- The first scheduled run fires.
- Drafts appear in chat (founder mode) OR a leads file appears at outputs/leads/YYYY-MM-DD.md (lead-scout mode).
- You approve in 10 minutes, posts go live (founder) or you DM the top leads manually (lead-scout).

⚡ Next move
Subject: First scheduled run
Verb: Watch it fire at <earliest-time> tomorrow
Timing: <tomorrow's date>, <earliest-time>
Why: You see if the schedule and the spec work end-to-end without the wizard babysitting them.
```

Exit.
