# Core Principle

This skill currently centers on one primary automation principle.

## Priority Order

### 1. BiDi-native behavior first

When `ruyiPage` exposes a BiDi-grounded interaction path, use that first for sensitive automation.

### 2. Full JS event-chain behavior second

If JS is the better interaction layer, it must not be a shortcut.

Requirements:

- model the full control-specific human-like event sequence
- include the `ruyi` property where required
- treat `isTrusted`-related behavior as part of the design target

### 3. Humanization is required

Automation behavior should avoid mechanical timing and repeated identical interaction patterns.

Expected qualities:

- bounded randomness
- humanized pacing
- natural pauses and sequencing
- realistic interaction ordering

### 4. Isolation is required

For new identities, prefer a fresh isolated `user_dir`.

### 5. Fingerprint consistency is required

If fingerprint changes are applied, they must remain internally consistent and aligned with the effective IP context.

### 6. Complex-page locating must stay resilient

For difficult pages, locating should not stop at a single selector guess.

Expected approach:

- probe for the real interactive target repeatedly
- adapt across iframe nesting
- handle dynamic entry points such as textarea, contenteditable, or custom input containers
- treat closed-shadow-like scenarios as locator-discovery problems that require fallback probing rather than fragile one-shot selection

This locating process should be evidence-driven.

- collect page source context first
- collect JS clues first
- collect network evidence when the page is dynamic
- then narrow down the actual interactive target

### 7. API grounding is required

When implementation details are uncertain:

- check the official GitHub repository first: <https://github.com/LoseNine/ruyipage>
- check the official `examples` directory first
- use local source copies only as a secondary reference
- if the local copy is behind, update it before relying on it
- only write APIs and calling patterns that can be grounded in those references

### 8. Locator strategy must be multi-layered

For difficult pages, combine multiple locating methods:

- XPath
- CSS
- DOM tree inspection such as `browsingContext.getTree`
- element geometry and center-point XY probing
- BiDi route and full-`ruyi` JS route side by side until one is proven workable
