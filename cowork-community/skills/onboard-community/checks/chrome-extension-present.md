# Check — Claude for Chrome present

## Purpose

The plugin uses Claude in Chrome (the official Claude for Chrome extension) to read community feeds and post approved drafts. Without it, no skill in this plugin can run.

## Verification flow

1. **Ask the user.** "Do you have the Claude for Chrome extension installed and signed in? (yes / no / not sure)"
2. **If 'not sure'** — give the verification steps:
   > "Open Chrome. Click the puzzle-piece icon in the top-right toolbar. Look for 'Claude for Chrome' in the list. If it's there and shows 'signed in,' you're good."
3. **If 'no'** — give the install steps:
   > "Open https://chrome.google.com/webstore. Search 'Claude for Chrome'. Click 'Add to Chrome'. Click the puzzle-piece icon, pin Claude for Chrome to the toolbar, click it, sign in with your Claude account. Then come back and tell me 'done'."
4. **Quick browser test** (only if the user says yes) — ask Claude in Chrome to navigate to `https://claude.ai`. If it loads, the extension is working.

## Pass criteria

The extension is installed, signed in, and a test navigation succeeds.

## Fail handling

If the user cannot install the extension (e.g. on a browser that doesn't support it):

> "Halt: this plugin requires the Claude for Chrome extension, which currently only runs on Chromium-based browsers (Chrome, Brave, etc.). If you're on Firefox or Safari, the plugin can't proceed yet. Firefox support is on the v0.2 roadmap. Switch browsers or wait for v0.2."

If the user says they have it installed but it isn't working:

> "Try: (1) Quit Chrome fully. (2) Reopen Chrome. (3) Click the Claude for Chrome icon. (4) Sign out, sign back in. (5) Try the test navigation again. If it still fails, the install is broken — reinstall the extension."

## Skip-allowed

If the user is doing a dry-run or planning install (not actually running yet), they can answer "I'll install later" and the wizard skips the browser test. State will mark `chrome_extension_status: deferred`. No skills will work until they install.
