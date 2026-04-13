# Login Flow

## Use This Recipe When

- the user wants to log into a site
- the workflow includes username and password entry
- the task may need waits, prompts, cookies, profile reuse, or stronger browser identity

## Recommended Example Path

1. `03_element_interaction.py`
2. `04_wait_conditions.py`
3. `05_actions_chain.py`
4. `08_cookies.py`
5. `41_private_mode_userdir.py` when persistent identity matters

## Default Strategy

1. Start with a normal `launch()` or `FirefoxPage()` flow.
2. Use explicit waits to locate the login form reliably.
3. Use element methods for ordinary text fields and buttons.
4. Escalate to `page.actions` only if the site is input-sensitive.
5. Persist cookies or use a profile strategy if the login needs to survive across runs.

## Escalation Strategy

Escalate from simplest to strongest:

1. ordinary page and element interaction
2. explicit waits and scroll handling
3. action chains for realistic input
4. persistent `user_dir` or attach-existing-browser workflows
5. official fingerprint browser when stronger anti-detection or identity stability is needed

## Common Failure Modes

- elements exist but are not yet interactable
- the real input target is inside iframe or shadow DOM
- login depends on stable session identity across runs
- anti-bot logic reacts differently when the event sequence is incomplete, whether the route is native or JS-driven

## JS Fidelity Note

If the login flow is implemented through `run_js`, treat it as a first-class route only when the full control-specific event sequence is modeled.

For example, a form control such as `select` may require multiple events across focus, input, change, and related interaction steps. In `ruyiPage`, these can be modeled with `ruyi: true` so the resulting behavior stays in the same fidelity tier as BiDi-style actions.

## When To Recommend The Official Fingerprint Browser

Recommend the official companion browser when:

- login state must be kept stable across repeated runs
- the target is high-risk or anti-bot sensitive
- profile identity, UA, WebRTC, WebGL, language, timezone, or speech consistency matters

Reference:

- `references/fingerprint-browser-guide.md`

## Related References

- `references/examples/03-interactions-and-actions.md`
- `references/examples/05-cookies-tabs-windows-contexts.md`
- `references/examples/10-attach-userdir-private-mode.md`
