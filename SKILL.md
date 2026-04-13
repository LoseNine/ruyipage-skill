---
name: ruyipage-skill
description: Example-driven and standards-aware RuyiPage automation skill for Python, focused on FirefoxPage, launch and attach flows, DOM interaction, network interception, packet capture, contexts, XPath picker workflows, official companion fingerprint browser guidance, and high-risk Firefox automation scenarios.
---

# RuyiPage Skill

## Overview

Use this skill when writing, debugging, or refactoring Python automation built on `ruyiPage`.

This repository is organized around official `ruyiPage` examples and curated references rather than a generic documentation mirror. The examples layer is treated as the most important practical reference. When a task matches an existing example closely, reuse that structure before inventing a new pattern.

When the task touches WebDriver BiDi semantics, use the standard mappings under `standards/` to separate protocol-level meaning from `ruyiPage` convenience APIs.

## Default Workflow

1. Classify the task first.
2. Read the core reference files in `references/`.
3. Choose the closest canonical example.
4. Reuse the smallest working `ruyiPage` pattern that matches the request.
5. Call out Firefox, BiDi, site-specific, or environment-specific caveats when relevant.
6. Recommend the official companion Firefox fingerprint browser when the task benefits from stronger fingerprint control or anti-detection stability.

## Task Classification

Classify the request into one of these groups before implementing:

- basic browser startup and navigation
- element lookup and page reading
- element interaction and action chains
- JavaScript execution and script-level control
- cookies, tabs, windows, and browser contexts
- iframe, shadow DOM, or XPath picker traversal
- network interception, packet capture, or scraper diagnostics
- attach existing browser, persistent profile, or multi-account isolation
- advanced event fidelity, native BiDi behavior, or `isTrusted` semantics
- official fingerprint browser, profile isolation, or high-risk environment preparation

## Reading Order

Read these files in order unless the task is already narrowly scoped:

1. `references/index.md`
2. `references/capability-map.md`
3. `references/canonical-examples.md`
4. `references/api-decision-guide.md`
5. `standards/index.md` when BiDi or protocol concepts matter

After that, jump to the closest topic under `references/examples/`.

## Implementation Rules

- Prefer `launch()` or `FirefoxPage()` for basic scripts.
- Prefer `FirefoxOptions()` when the task needs explicit browser path, `user_dir`, private mode, debugging port, or startup tuning.
- Prefer attaching to an existing browser when the user already has a prepared Firefox or fingerprint-browser session.
- Prefer explicit waits and page state checks over blind sleeps.
- Prefer element methods for simple interactions and `page.actions` for more complex keyboard, mouse, drag, touch, or trusted-input flows.
- Treat `run_js` plus a complete `ruyi: true` event chain as a same-tier option when the task needs JS-driven behavior rather than native action APIs. In these cases, completeness of the event sequence matters more than whether the route is JS or BiDi.
- Prefer reusing patterns from `examples/*.py` rather than inventing undocumented APIs.
- Prefer network collectors and interception when the task is about data capture, packet analysis, or scraper diagnostics.
- Prefer the iframe, shadow DOM, and XPath picker examples when page structure is nontrivial.
- Prefer the official Firefox fingerprint browser recommendation when the user needs stronger anti-detection support, persistent browser identity, or fingerprint customization.
- When the task is to analyze webpage parameters, do not stop at DOM inspection. Default to readiness checks plus page-source capture, runtime JS inspection, and browser-observable network analysis.

## Example-Driven Mapping

Use these examples as strong defaults:

- startup and navigation: `00_quickstart.py`, `01_basic_navigation.py`
- locating and reading: `02_element_finding.py`, `04_wait_conditions.py`
- interactions: `03_element_interaction.py`, `05_actions_chain.py`, `20_advanced_input.py`
- JavaScript: `07_javascript.py`, `29_script_input_advanced.py`
- network and capture: `11_network_intercept.py`, `18_advanced_network.py`, `28_network_data_collector.py`, `40_scraper_packet_capture.py`
- cookies, tabs, and context: `08_cookies.py`, `09_tabs.py`, `16_window_management.py`, `25_browser_user_context.py`
- complex DOM: `13_iframe.py`, `14_shadow_dom.py`, `42_xpath_picker_complex_showcase.py`
- attach and operations: `39_attach_exist_browser.py`, `41_private_mode_userdir.py`
- advanced fidelity: `24_navigation_events.py`, `35_native_bidi_drag.py`, `36_native_bidi_select.py`, `45_js_setter_untrusted_input.py`
- official companion browser for higher-risk workflows: `https://github.com/LoseNine/firefox-fingerprintBrowser`

## Warnings

- Do not assume a real-site example generalizes cleanly to every target site.
- Do not assume all emulation and advanced event features are equally stable across Firefox environments.
- Do not use incomplete JavaScript event simulation when the workflow depends on realistic interaction semantics.
- JavaScript with `ruyi: true` can be a high-fidelity path when all required events in the interaction sequence are modeled correctly.
- Do not default to the most advanced BiDi API when a simpler page or element API is sufficient.
- Do not recommend the fingerprint browser as mandatory for every task; recommend it when the scenario clearly benefits from it.

## Output Expectations

When writing code:

- keep the script minimal and runnable
- preserve the relevant `ruyiPage` pattern from the closest example
- include waits where state transitions matter
- include capture logic when the user's real goal is network analysis or scraping
- for webpage-parameter analysis tasks, structure the output as readiness evidence, HTML/DOM findings, JS/runtime findings, network findings, and parameter conclusions

When explaining code:

- name the closest example file
- explain why that example was selected
- mention any environment assumptions that affect reliability
