# Phase 3 — Pull your voice + your business

## Ask

This phase reads `about-me/writing-rules.md` and `about-me/business-brain.md` and surfaces what it sees for user confirmation. Generic replies sound like a bot. We bake the user's voice into every spec at write time.

1. Read `about-me/writing-rules.md`. Pull out:
   - Top 3–5 tone rules (one-liners)
   - Banned phrases (kill list)
   - Sentence-rhythm rules
   - Signature moves

Show them: "Here's what I see for your voice: <bullets>. Sound right?"

If yes, continue. If something is off, ask: "What should I add or change?" Update the file (with approval) and re-read.

2. Read `about-me/business-brain.md`. Pull out:
   - Top 3 offers (with prices if listed)
   - ICP one-liner
   - Top 3 pain points (in ICP's exact words)
   - 3 free-content touchpoints (latest video, lead magnet, etc.)

Show them: "Here's what I see for your business: <bullets>. Sound right?"

If yes, continue. If something is off, ask: "What should I add or change?" Update the file (with approval) and re-read.

3. **Lead-scout check.** If any community in state has `role: lead-scout`, also confirm: "For lead-scout mode, I need at least 3 pain phrases — the actual phrases your ICP uses when they're frustrated. I see: <list>. Add any more?"

The wizard needs at least 3 pain phrases to enable lead-scout scoring. If `business-brain.md` has fewer, prompt the user to add more before proceeding.

## Write

Update `state-community.md` with the pulled values for later use in Phase 4:

```yaml
voice_summary:
  tone: ["...", "...", "..."]
  banned: ["...", "...", "..."]
  rhythm: "..."
  signature: ["...", "..."]
business_summary:
  offers: [{name: "...", price: "..."}, ...]
  icp: "..."
  pains: ["...", "...", "..."]
  touchpoints: ["...", "...", "..."]
```

## Next

Move to Phase 4 — spec build. Tell the user: "Voice + business locked. Next I'll generate one spec file per community, customized per platform. Takes about 90 seconds per community."
