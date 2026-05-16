# Phase 4 — Build the per-community spec (one per community)

## Ask

For each community in state (loop), generate one spec file. The template depends on `role`. The platform module from `platforms/<platform>.md` drives the platform-specific questions.

For each community:

1. **Load the right template.**
   - `role: founder` → `templates/founder-spec.md`
   - `role: lead-scout` → `templates/lead-scout-spec.md`

2. **Load the right platform module.**
   - `platform: skool` → `platforms/skool.md`
   - `platform: facebook` → `platforms/facebook.md`
   - … (one per supported platform)
   - `platform: other` → `platforms/generic.md`

3. **Ask the platform-specific questions** listed in the platform module. Usually 2–4 short questions.

4. **Ask role-specific questions:**

   **For `founder` communities:**
   - "Pick your 3 funnel touches. I see in your business-brain.md: <touchpoints>. Pick 3 or write 3 different ones."
   - "Pick your 7-day post rotation. Monday through Sunday. I can suggest a default — want it?"
   - "Anything you NEVER want the agent to post about? (Common: medical advice, legal advice, competitor names.)"

   **For `lead-scout` communities:**
   - "I'll scan for posts matching these pain phrases: <list from voice_summary>. Add any more specific to this community?"
   - "What 'recommendation' phrases signal a lead? Example: 'looking for someone who...', 'who do you use for X'. Want defaults?"
   - "Skip posts with these flags: <platform-specific defaults>. Add any more?"

5. **Generate the spec file.** Fill in all `{{placeholders}}` in the template with the user's actual answers + voice + business pulls from Phase 3. Show the user the final file. Ask: "Save this to `projects/community-engagement/<slug>.md`?"

6. **Save on approval.** If the user wants edits first, apply them inline and re-show. Save only after explicit yes.

Loop until all communities in state have a spec.

## Write

For each approved spec, write the file to `projects/community-engagement/<slug>.md`. Update state:

```yaml
communities:
  - slug: "<slug>"
    spec_status: "ok"
    spec_path: "projects/community-engagement/<slug>.md"
```

## Next

Move to Phase 5 — schedule. Tell the user: "<N> specs written. Next I'll create one scheduled task per community so they fire every weekday. Takes 10 seconds per community."
