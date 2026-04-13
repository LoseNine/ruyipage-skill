# Multi-Account Isolation

## Use This Recipe When

- the user needs multiple accounts at once
- sessions must not leak between accounts
- one browser process is not enough because identity separation matters

## Recommended Example Path

1. `25_browser_user_context.py`
2. `37_three_isolated_user_context_tabs.py`
3. `41_private_mode_userdir.py`

## Default Strategy

1. Decide whether isolation is needed within one browser runtime or across separate persistent profiles.
2. Use user contexts when same-runtime isolation is sufficient.
3. Use separate `user_dir` or separate browser instances when persistence or stronger separation is required.
4. Keep account-specific actions clearly tied to the right context or profile.

## Decision Rule

- use tabs only when shared session state is acceptable
- use user contexts when logical isolation is needed in one browser environment
- use separate profiles or the official fingerprint browser when stronger persistent identity separation is required

## Common Failure Modes

- using tabs when actual cookie isolation is required
- mixing actions across contexts and corrupting the intended account state
- treating temporary isolation as equivalent to long-lived profile isolation

## When To Recommend The Official Fingerprint Browser

Recommend it when the user wants the strongest practical per-profile separation and fingerprint consistency across multiple accounts.

## Related References

- `references/examples/05-cookies-tabs-windows-contexts.md`
- `references/examples/10-attach-userdir-private-mode.md`
- `references/fingerprint-browser-guide.md`
