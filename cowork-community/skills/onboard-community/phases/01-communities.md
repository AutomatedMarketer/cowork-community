# Phase 1 — Add your communities

## Ask

Tell the user we're going to collect their communities one at a time. For each community ask, in order:

1. **Name.** "What's the community name? (Example: My Skool Group)"
2. **Platform.** "What platform? Pick one: skool / facebook / circle / discord / slack / linkedin / reddit / mighty / other"
3. **URL.** "What's the full URL? (Example: https://www.skool.com/my-group)"
4. **Role.** "Are you the founder of this community, or a member scouting for leads? Pick: founder / lead-scout"
5. **Slug confirmation.** Generate a kebab-case slug from the name (e.g. "My Skool Group" → `my-skool-group`). Confirm: "I'll save this as `<slug>.md`. Cool, or pick a different slug?"
6. **Another?** "Add another community, or move on?"

Loop until the user says "move on." Show a recap of all communities added so far before moving to Phase 2.

## Validation rules

- **Platform** must be one of the 9 supported values. If "other," ask one extra question: "What's the platform name? (For my notes — I'll treat it as generic-web.)"
- **URL** must start with `http://` or `https://`. If not, prompt to fix.
- **Slug** must be lowercase letters, digits, and hyphens only. No spaces, no special chars. Suggest a normalized version if needed.
- **Duplicate slug** in `state-community.md` — refuse and ask for a different one.

## Write

For each community confirmed, append to `state-community.md`:

```yaml
communities:
  - name: "<name>"
    slug: "<slug>"
    platform: "<platform>"
    url: "<url>"
    role: "<founder | lead-scout>"
    spec_status: "pending"
    schedule_status: "pending"
```

Update `current_phase` and `last_updated` at the end of the phase.

## Next

Move to Phase 2 — browser check. Tell the user: "Got <N> communities. Next I'll test that Claude in Chrome can actually see each one. Takes about 30 seconds per community."
