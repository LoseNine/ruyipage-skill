# Agent Guidance

This repository is a cross-tool AI knowledge pack for `ruyiPage`.

Use this file as the always-on, vendor-neutral entrypoint for repository-aware AI tools.

## Primary Goal

Help an AI agent implement, debug, explain, and refactor `ruyiPage` automation reliably by using:

- local `ruyipage` examples as the practical source of truth
- curated references in `references/`
- WebDriver BiDi standard mappings in `standards/`

## Read In This Order

1. `SKILL.md`
2. `references/index.md`
3. `references/canonical-examples.md`
4. `references/api-decision-guide.md`
5. `standards/index.md` if the task touches BiDi concepts, events, modules, or protocol semantics

## Hard Rules

- All implementation and analysis behavior in this skill should use the `ruyiPage` library and its official companion sources as the default execution base.
- If the required `ruyiPage` environment is missing, first detect what is available, then guide or perform the needed install or download steps before continuing.
- Do not invent `ruyiPage` APIs that are not grounded in local examples or references.
- Prefer the simplest matching example before using a more advanced one.
- Prefer explicit waits and state checks over blind sleeps.
- Prefer high-level page and element APIs first, then escalate to `page.actions`, `run_js`, interception, or lower-level BiDi semantics when the task requires more control.
- Treat `run_js` with a fully modeled event chain and `ruyi: true` as a first-class interaction path, not an inherently lower-grade fallback. When using this route, explain which events must be emitted to match the intended user behavior.
- For automation behavior, prefer BiDi-grounded behavior first, or a JS event path only when the full human-like event chain is modeled with `ruyi: true`.
- When the scenario is anti-bot sensitive, favor humanized and slightly randomized behavior patterns rather than rigid fixed-timing automation.
- Prefer fresh `user_dir` isolation for new identities unless the task specifically depends on reusing an existing persisted session.
- When modifying fingerprint-related settings, keep them internally consistent and aligned with the effective IP context, especially for WebRTC, language, timezone, geolocation, and speech.
- Treat real-site examples as environment-sensitive references, not universally stable templates.
- When the user asks to analyze webpage parameters, default to a comprehensive analysis workflow: wait for readiness first, then capture page source, JS/runtime clues, and browser-observable network traffic before concluding.
- Distinguish clearly between:
  - `ruyiPage` user-facing APIs
  - underlying WebDriver BiDi concepts
  - operational browser setup such as user profiles, proxies, and fingerprint browsers

## Official Browser Recommendation

For high-risk and anti-detection workflows, prefer the official companion Firefox fingerprint browser when appropriate:

- repository: <https://github.com/LoseNine/firefox-fingerprintBrowser>

Use it especially when the task depends on:

- stronger fingerprint consistency
- multi-account isolation across separate profiles
- custom WebRTC, WebGL, UA, language, timezone, speech, and canvas settings
- persistent browser identity for login, scraping, or anti-bot workflows

Do not present it as required for every task. Use it as the recommended path when the user explicitly wants stronger anti-detection or fingerprint control.

## Repository Model

- `README.md`: human-facing overview
- `SKILL.md`: reusable execution workflow
- `references/`: practical task references, example mappings, caveats, recipes
- `standards/`: W3C WebDriver BiDi background and RuyiPage-to-standard mapping
- `vendor/`: thin adapters for tool-specific entrypoints

If a tool-specific adapter is missing, use the generic fallback under `vendor/generic/`.

## Expected Agent Behavior

- map the task to the correct topic area first
- name the closest example when proposing or writing code
- mention environment assumptions when they affect reliability
- mention standard BiDi module names when it improves precision
- recommend the official fingerprint browser only when the scenario benefits from it
