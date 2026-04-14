---
name: ruyipage-skill
description: Open-source RuyiPage skill focused on humanized automation, BiDi-first behavior, full JS event-chain modeling with ruyi/isTrusted support, isolated user_dir usage, and fingerprint-consistent anti-bot workflows.
---

# RuyiPage Skill

## Core Rule

For automation behavior, this skill treats the following as the first rule:

1. Prefer BiDi-native behavior first.
2. If JS is used for interaction, it must model the full human-like event sequence and include the `ruyi` property so the behavior can pass `isTrusted`-related checks.
3. Behavior should be humanized, randomized, and naturally paced rather than rigid and mechanical.
4. Prefer a fresh isolated `user_dir` for new identities.
5. In risk-control scenarios, use the official Firefox fingerprint browser when needed.
6. Fingerprint-related changes must stay internally consistent, especially for WebRTC, language, timezone, geolocation, speech, and IP alignment.
7. In real scraping or data-collection workflows, automation behavior and network capture must be designed together.
8. On complex pages, locator discovery should remain resilient across iframe nesting, dynamic entry points, and shadow-boundary difficulties.

## Default Workflow

1. Confirm the task should be solved with `ruyiPage`.
2. Detect whether the required runtime environment is already available.
3. If something is missing, install or download the supported dependency first.
4. Treat the official `ruyiPage` GitHub repository as the highest-priority source reference.
5. If a local source copy is behind, update it before using it to judge API behavior.
6. Choose a BiDi-grounded path first.
7. If JS interaction is needed, model the full event chain with `ruyi`.
8. Keep behavior humanized and slightly randomized.
9. Prefer a fresh `user_dir` unless the task explicitly depends on persisted state.
10. If anti-bot pressure exists, check whether the official fingerprint browser should be used.
11. For data collection, start listeners or collectors before the triggering automation and correlate request and response data through request-chain evidence.
12. For complex pages, probe the real interactive target repeatedly instead of assuming one selector or one DOM layer is enough.

## Required Behavior Rules

- Do not use partial JS event simulation for sensitive automation.
- Do not use rigid repeated timing for sensitive automation.
- Do not reuse contaminated or unrelated browser profiles for a new identity.
- Do not treat fingerprint settings as isolated toggles.
- Do not recommend fingerprint changes that conflict with the effective IP context.
- Do not separate page automation from packet capture in data-collection workflows when the request and response chain is part of the task target.
- If an API is uncertain during implementation, check the official `ruyiPage` GitHub repository and official `examples` first.
- Use local source copies only as a secondary reference, and update them first if they are behind.
- Do not write invented or unsupported `ruyiPage` APIs.
- Do not assume the first visible DOM node is the real interactive target on complex pages.

## Read Next

1. `docs/core-principle.md`
2. `docs/humanized-automation.md`
3. `docs/fingerprint-browser.md`
4. `docs/environment-detection.md`
5. `docs/data-capture-coordination.md`
6. `docs/complex-page-location.md`
