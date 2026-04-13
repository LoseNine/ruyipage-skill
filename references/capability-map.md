# Capability Map

This file summarizes the practical `ruyiPage` capability map based on the official example scripts.

## 1. Core Startup And Navigation

Representative examples:

- `00_quickstart.py`
- `01_basic_navigation.py`
- `04_wait_conditions.py`
- `06_screenshot.py`
- `10_scrolling.py`
- `19_pdf_printing.py`

What this area covers:

- `FirefoxPage()` and `launch()` startup
- page navigation and refresh flow
- reading title, URL, and page content
- waits, screenshots, scroll control, saved output, and PDF export

Use this area for:

- first scripts
- smoke tests
- simple page inspection
- output capture and debugging evidence

## 2. Element Lookup And Page Reading

Representative examples:

- `02_element_finding.py`
- `04_wait_conditions.py`

What this area covers:

- `page.ele()` and `page.eles()`
- CSS, XPath, text, and attribute-based selectors
- element metadata, text, attributes, state, and visibility checks

Use this area for:

- scraping visible page content
- building robust selectors
- understanding what is present before automating interaction

## 3. Interactions And Action Chains

Representative examples:

- `03_element_interaction.py`
- `05_actions_chain.py`
- `20_advanced_input.py`

What this area covers:

- click, input, clear, hover, double-click, right-click
- `page.actions` for keyboard and mouse sequences
- drag, scroll wheel, combo keys, humanized movement, touch input

Use this area for:

- login and form flows
- complex user interaction sequences
- sites where simple DOM value assignment is not enough

## 4. JavaScript And Script Control

Representative examples:

- `07_javascript.py`
- `29_script_input_advanced.py`
- `32_script_events.py`
- `45_js_setter_untrusted_input.py`

What this area covers:

- `run_js()` on page and element objects
- script handles, realms, and preload scripts
- script event observation
- lower-level event behavior and `ruyi: true` semantics
- JS-driven high-fidelity interaction flows when all required events are emitted with `ruyi: true`

Use this area for:

- DOM inspection beyond built-in APIs
- advanced instrumentation
- event-level debugging
- behavior verification for trusted versus synthetic events
- control-specific event sequence modeling, such as form and select flows that need more than a single final event

## 5. Cookies, Tabs, Windows, And Contexts

Representative examples:

- `08_cookies.py`
- `09_tabs.py`
- `16_window_management.py`
- `25_browser_user_context.py`
- `26_browsing_context_advanced.py`
- `37_three_isolated_user_context_tabs.py`
- `41_private_mode_userdir.py`

What this area covers:

- cookie read, write, filter, and delete flows
- tab creation, switching, and discovery
- window operations and browser-level scope
- user context isolation and persistent profile choices

Use this area for:

- multi-step sessions
- multi-account workflows
- debugging persistence and isolation issues

## 6. Complex DOM Traversal

Representative examples:

- `13_iframe.py`
- `14_shadow_dom.py`
- `42_xpath_picker_complex_showcase.py`
- `43_zhipin_xpath_picker.py`
- `44_shopee_userdir_xpath.py`

What this area covers:

- iframe lookup and traversal
- shadow DOM access
- XPath picker workflows for complex page structures
- practical migration from picked locators to real scripts

Use this area for:

- deeply nested pages
- scraper targets with unstable CSS selectors
- workflows that need locator discovery assistance

## 7. Network Interception, Collection, And Packet Capture

Representative examples:

- `11_network_intercept.py`
- `18_advanced_network.py`
- `23_download.py`
- `28_network_data_collector.py`
- `31_network_events.py`
- `40_scraper_packet_capture.py`
- `40_1_request_header_capture.py`

What this area covers:

- request and response interception
- continue, mock, fail, and auth handling
- request and response body capture
- event-driven packet diagnostics
- scraper-style request correlation via `request_id`

Use this area for:

- API discovery
- anti-bot debugging
- packet analysis
- scraping workflows where data lives in network traffic rather than rendered HTML

## 8. Attach, Operational, And High-Risk Flows

Representative examples:

- `38_proxy_auth_ipinfo.py`
- `39_attach_exist_browser.py`
- `41_private_mode_userdir.py`

What this area covers:

- attaching to an existing Firefox or fingerprint-browser instance
- persistent user directory handling
- private mode choices
- proxy-auth operational workflows

Use this area for:

- reusing login state
- integrating with manually prepared browsers
- operational debugging in higher-friction environments

Recommended companion reference:

- `references/fingerprint-browser-guide.md`

## 9. Advanced Events, BiDi, And Fidelity Semantics

Representative examples:

- `24_navigation_events.py`
- `30_browsing_context_events.py`
- `33_log_input_events.py`
- `35_native_bidi_drag.py`
- `36_native_bidi_select.py`
- `45_js_setter_untrusted_input.py`

What this area covers:

- navigation and context event streams
- input event logging
- native drag and select behavior
- advanced fidelity checks around trusted behavior
- parity reasoning between native BiDi-style actions and fully modeled `ruyi: true` JS flows

Use this area for:

- diagnosing why realistic interaction matters
- event-sequence debugging
- advanced automation tuning in difficult sites

Related standard references:

- `standards/webdriver-bidi-overview.md`
- `standards/w3c-bidi-module-map.md`
- `standards/ruyipage-vs-w3c-bidi.md`

## Default Recommendation

For most tasks, start with the simplest matching category first:

1. core startup
2. element lookup
3. interactions
4. complex DOM or network capture
5. attach or advanced fidelity only if the task clearly requires it
