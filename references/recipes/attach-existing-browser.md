# Attach Existing Browser

## Use This Recipe When

- the user already has a running browser session
- login state already exists in a manually prepared browser
- the workflow depends on taking over an existing Firefox or companion fingerprint browser instance

## Recommended Example Path

1. `39_attach_exist_browser.py`
2. `41_private_mode_userdir.py`
3. `25_browser_user_context.py` when isolation also matters

## Default Strategy

1. Confirm that the browser already contains the needed state.
2. Attach instead of recreating the full setup in script.
3. Validate that the target tab, context, or session is the intended one.
4. Continue with ordinary page automation only after attach succeeds.

## Why This Recipe Exists

Some workflows are difficult because of environment setup, not because of page automation itself.

Attach mode lets the AI separate:

- browser preparation
- session reuse
- page automation after takeover

## Common Failure Modes

- the attached browser is not the intended instance
- the existing state lives in a different profile than expected
- attach succeeds but the page state is stale or in the wrong tab

## When To Recommend The Official Fingerprint Browser

Recommend the official companion browser when the user wants:

- manually prepared anti-detection browser identity
- persistent fingerprint-controlled login state
- stronger per-profile isolation across accounts

## Related References

- `references/examples/10-attach-userdir-private-mode.md`
- `references/fingerprint-browser-guide.md`
