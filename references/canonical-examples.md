# Canonical Examples

This file lists the most useful example scripts in `E:\ruyipage\examples` and explains when to start from each one.

## First-Line Examples

### `00_quickstart.py`

Start here when you need the smallest possible working script.

Use for:

- opening a page
- reading title
- validating environment setup

### `02_element_finding.py`

Start here when the task is primarily about selectors and extracting information from the DOM.

Use for:

- selector design
- locating elements reliably
- reading text, attributes, and element state

### `03_element_interaction.py`

Start here when the task is mainly clicks, inputs, and normal page controls.

Use for:

- form filling
- button clicks
- simple interaction scripts

### `05_actions_chain.py`

Start here when the task involves keyboard or mouse sequences rather than isolated element methods.

Use for:

- combo keys
- movement-based flows
- chained interaction sequences

### `07_javascript.py`

Start here when built-in APIs are not enough and you need direct JavaScript execution.

Use for:

- DOM inspection
- custom JS evaluation
- advanced page-side diagnostics
- building JS-side control flows that may later need `ruyi: true` events

### `11_network_intercept.py`

Start here when the task is about intercepting traffic and understanding the basic interception lifecycle.

Use for:

- beginner network interception
- request or response inspection
- mock or fail experiments

### `13_iframe.py`

Start here when the page structure includes iframe boundaries.

Use for:

- frame traversal
- locating content inside embedded documents

### `14_shadow_dom.py`

Start here when the target element is inside shadow DOM.

Use for:

- open or special shadow-root access patterns
- complex DOM boundary traversal

### `18_advanced_network.py`

Start here when basic interception is not enough.

Use for:

- request manipulation
- response continuation
- advanced interception strategies

### `20_advanced_input.py`

Start here when interaction fidelity matters more than simple convenience.

Use for:

- advanced keyboard and mouse behavior
- drag, hover, touch, combo keys, and trusted-input patterns
- comparing native high-fidelity input with script-driven alternatives

### `28_network_data_collector.py`

Start here when the real target is collecting request or response bodies for downstream analysis.

Use for:

- API response capture
- scraper packet collection
- request-response correlation

### `40_scraper_packet_capture.py`

Start here when the user is building a scraper and needs page automation plus structured packet capture together.

Use for:

- real scraping workflows
- network-backed data extraction
- correlating browser actions with captured traffic

## Strong Secondary Examples

These are often the next file to consult after the first-line examples:

- `01_basic_navigation.py`
- `04_wait_conditions.py`
- `08_cookies.py`
- `09_tabs.py`
- `16_window_management.py`
- `24_navigation_events.py`
- `25_browser_user_context.py`
- `29_script_input_advanced.py`
- `31_network_events.py`
- `39_attach_exist_browser.py`
- `41_private_mode_userdir.py`
- `42_xpath_picker_complex_showcase.py`

## Advanced References

These are important, but should not be the default starting point for ordinary automation tasks:

- `30_browsing_context_events.py`
- `32_script_events.py`
- `33_log_input_events.py`
- `35_native_bidi_drag.py`
- `36_native_bidi_select.py`
- `45_js_setter_untrusted_input.py`

Use these when:

- debugging event fidelity
- explaining `isTrusted` behavior
- explaining `ruyi: true` event modeling and complete JS interaction chains
- dealing with native BiDi edge behavior
- investigating lower-level browser behavior rather than just automating a page

## Real-Site Or Environment-Dependent Examples

Treat these carefully because they depend more heavily on live sites, login state, proxy setup, or persistent profiles:

- `21_mobile_google_emulation.py`
- `38_proxy_auth_ipinfo.py`
- `40_1_request_header_capture.py`
- `43_zhipin_xpath_picker.py`
- `44_shopee_userdir_xpath.py`

These can still be very valuable, but they should usually be adapted rather than copied directly.
