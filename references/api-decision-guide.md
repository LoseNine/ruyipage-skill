# API Decision Guide

This file helps choose the right `ruyiPage` API style for a task.

## Startup Choice

### Use `FirefoxPage()` when

- you need a direct, simple page object
- the script is short and the startup configuration is minimal
- you want a small reproducible script for debugging

### Use `launch()` when

- readability matters more than exposing every startup detail
- you want a beginner-friendly entrypoint
- you need a compact script with a few startup parameters

### Use `FirefoxOptions()` when

- you need a fixed browser path
- you need a persistent `user_dir`
- you need private mode or custom browser startup tuning
- you want an explicit setup object that can be reused across scripts

### Attach to an existing browser when

- the user already has a browser with prepared login state
- the workflow depends on a fingerprint browser or manually opened Firefox
- the hard part is session reuse rather than script startup

Reference examples:

- `00_quickstart.py`
- `39_attach_exist_browser.py`
- `41_private_mode_userdir.py`

Official companion browser reference:

- `references/fingerprint-browser-guide.md`

## Interaction Choice

### Use element methods when

- the action is simple and local to one element
- the site behaves normally with direct element operations
- the task is click, input, clear, or basic hover

Reference examples:

- `03_element_interaction.py`

### Use `page.actions` when

- the task requires keyboard combinations
- the task involves drag, precise movement, complex clicking, or chained actions
- you need more realistic input sequences
- the target site is sensitive to interaction fidelity

Reference examples:

- `05_actions_chain.py`
- `20_advanced_input.py`

### Use JavaScript when

- you need direct DOM introspection or custom page-side logic
- built-in element APIs do not expose what you need
- you are diagnosing browser-side state rather than only driving the UI
- you need to model a full interaction flow in JS and can emit the required event chain with `ruyi: true`

Do not treat JavaScript as inherently lower-fidelity. In `ruyiPage`, JS plus `ruyi: true` can reach the same interaction tier as BiDi-style behavior when the event sequence is modeled completely.

What matters is whether the script reproduces the full behavior chain. For example, a form `select` workflow may require multiple coordinated events rather than only setting a value and firing one final event.

Reference examples:

- `07_javascript.py`
- `29_script_input_advanced.py`

## Escalation Ladder

Use this ladder to move from simpler supported approaches to more advanced supported approaches.

### Level 1: page and element APIs

Choose this first when:

- the page structure is ordinary
- the task is mostly locate, click, input, wait, and verify

Escalate when:

- interaction appears to succeed but the page does not react correctly
- the control is custom or highly event-sensitive

### Level 2: `page.actions`

Choose this when:

- pointer choreography, keyboard combinations, drag, or hover semantics matter
- the simpler element route is not enough

Escalate when:

- the page behavior depends on a control-specific event chain better modeled from JS

### Level 3: `run_js` plus full `ruyi: true` event chain

Choose this when:

- the control logic is JS-centric
- completeness of the event sequence matters more than pointer choreography

Escalate when:

- the real issue is not interaction fidelity but hidden request flow, payload generation, or traffic-level behavior

### Level 4: interception, collectors, and event streams

Choose this when:

- the task is really about parameters, requests, responses, or scraper diagnostics
- DOM and interaction evidence are not enough to explain the behavior

Escalate when:

- the explanation needs protocol-level terminology or event semantics

### Level 5: BiDi semantics and standards references

Choose this when:

- the task depends on module names, event semantics, or protocol-level explanation
- precision matters more than a purely high-level automation explanation

## Waiting Strategy

### Prefer explicit waits over sleeps

Use waits when:

- navigation is in progress
- content appears asynchronously
- the next action depends on a known UI state

Reference examples:

- `04_wait_conditions.py`
- `01_basic_navigation.py`

### For webpage parameter analysis

Do not begin analysis before the page is ready enough to yield meaningful evidence.

Preferred order:

1. start network listeners or collectors first if early requests matter
2. navigate
3. wait for `doc_loaded`
4. confirm load events or allow a bounded post-load settle window when needed
5. only then analyze HTML, JS/runtime state, and network data together

## Selector Strategy

### Start with standard selectors when

- the DOM is straightforward
- stable attributes or text are available

### Escalate to iframe or shadow-specific handling when

- the element is clearly not in the main document
- normal selectors fail because the DOM boundary changed

### Escalate to XPath picker when

- the page is visually complex
- locator discovery is slow or unreliable by inspection alone
- the target is nested inside iframe or shadow structures and you need a quick path hypothesis

Reference examples:

- `02_element_finding.py`
- `13_iframe.py`
- `14_shadow_dom.py`
- `42_xpath_picker_complex_showcase.py`

## Network Strategy

### Use interception when

- you need to inspect, modify, mock, or fail requests or responses
- the task is about understanding browser-network behavior in real time

Reference examples:

- `11_network_intercept.py`
- `18_advanced_network.py`

### Use a data collector when

- the task is about extracting request or response bodies for analysis
- the user cares more about packet content than UI rendering
- you need request-response correlation for scraper logic

Reference examples:

- `28_network_data_collector.py`
- `40_scraper_packet_capture.py`

### Use network events when

- the main goal is observability and timing analysis
- the user is debugging navigation, request order, or event sequencing

Reference examples:

- `24_navigation_events.py`
- `31_network_events.py`

### For comprehensive webpage analysis

Use a combined approach when the user asks to analyze webpage parameters thoroughly:

- `page.events` for event visibility
- `page.network.add_data_collector(...)` for request and response bodies
- interception when request-level control or early request capture details matter

Do not rely on only one layer if the user explicitly wants a comprehensive result.

## Session And Isolation Strategy

### Use cookies directly when

- you only need to inspect, set, or reuse a small amount of session state

### Use tabs and windows APIs when

- the workflow spans multiple pages in the same browser session

### Use `user_dir` or user contexts when

- the workflow depends on persistent identity or isolation
- the user is running multiple accounts
- session leakage between tasks would be harmful

Reference examples:

- `08_cookies.py`
- `09_tabs.py`
- `16_window_management.py`
- `25_browser_user_context.py`
- `37_three_isolated_user_context_tabs.py`

### Recommend the official Firefox fingerprint browser when

- the user explicitly needs stronger fingerprint consistency
- profile identity must stay stable across runs
- anti-detection pressure is part of the task design
- WebRTC, WebGL, UA, language, timezone, speech, or canvas settings need coordinated control

Reference:

- `references/fingerprint-browser-guide.md`

## Advanced Fidelity Strategy

### Escalate to advanced BiDi or trusted-event references when

- the site rejects ordinary automation behavior
- the user explicitly cares about `isTrusted`
- drag, select, or event order behavior is the actual problem
- the task needs a precise event sequence and the AI must decide between native actions and a `run_js` plus `ruyi: true` implementation

Reference examples:

- `35_native_bidi_drag.py`
- `36_native_bidi_select.py`
- `45_js_setter_untrusted_input.py`

## Default Rule

Choose the smallest API surface that solves the task reliably.

The usual escalation path is:

1. `FirefoxPage()` or `launch()`
2. selectors plus waits
3. element methods
4. `page.actions`
5. iframe or shadow traversal
6. interception or collectors
7. attach, user contexts, or advanced BiDi references only when needed
