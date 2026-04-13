# Example To Capability Matrix

This matrix ensures every local example under `E:\ruyipage\examples` has a documented place in the skill.

| Example | Primary Area | Notes |
|---|---|---|
| `00_quickstart.py` | core startup | smallest working entrypoint |
| `01_basic_navigation.py` | navigation and waits | page movement and state |
| `02_element_finding.py` | elements and locators | selector and inspection baseline |
| `03_element_interaction.py` | interactions | simple clicks and inputs |
| `04_wait_conditions.py` | navigation and waits | explicit wait patterns |
| `05_actions_chain.py` | interactions and actions | keyboard and pointer chains |
| `06_screenshot.py` | core startup | evidence capture |
| `07_javascript.py` | javascript and script | `run_js` baseline |
| `08_cookies.py` | cookies and contexts | session state |
| `09_tabs.py` | cookies and contexts | multi-tab workflows |
| `10_scrolling.py` | navigation and waits | viewport control |
| `11_network_intercept.py` | network and capture | interception baseline |
| `12_console_listener.py` | console and observability | log capture |
| `13_iframe.py` | iframe shadow xpath | frame traversal |
| `14_shadow_dom.py` | iframe shadow xpath | shadow traversal |
| `15_comprehensive.py` | overview | recap rather than first stop |
| `16_window_management.py` | cookies and contexts | windows and rect state |
| `17_user_prompts.py` | prompts and browser control | dialogs and prompt handlers |
| `18_advanced_network.py` | network and capture | advanced interception |
| `19_pdf_printing.py` | output artifacts | print and PDF |
| `20_advanced_input.py` | interactions and actions | broadest input surface |
| `21_emulation.py` | emulation and browser control | override capability survey |
| `21_mobile_google_emulation.py` | emulation and browser control | real-site mobile example |
| `22_web_extension.py` | browser control | web extension niche workflow |
| `23_download.py` | downloads and browser control | download lifecycle |
| `24_navigation_events.py` | advanced bidi and trusted events | navigation event model |
| `25_browser_user_context.py` | cookies and contexts | user context control |
| `26_browsing_context_advanced.py` | cookies and contexts | advanced browsing contexts |
| `27_emulation_advanced.py` | emulation and browser control | deeper emulation verification |
| `28_network_data_collector.py` | network and capture | payload collection |
| `29_script_input_advanced.py` | javascript and script | script input and advanced JS |
| `30_browsing_context_events.py` | advanced bidi and trusted events | browsing context events |
| `31_network_events.py` | network and capture | event-driven network observation |
| `32_script_events.py` | javascript and script | script events |
| `33_log_input_events.py` | advanced bidi and trusted events | input event logging |
| `34_remaining_commands.py` | overview | coverage appendix |
| `35_native_bidi_drag.py` | advanced bidi and trusted events | native drag fidelity |
| `36_native_bidi_select.py` | advanced bidi and trusted events | native select fidelity |
| `37_three_isolated_user_context_tabs.py` | cookies and contexts | multi-account isolation |
| `38_proxy_auth_ipinfo.py` | attach and operational flows | proxy-auth environment example |
| `39_attach_exist_browser.py` | attach and operational flows | attach baseline |
| `40_1_request_header_capture.py` | network and capture | real-site request header diagnostics |
| `40_scraper_packet_capture.py` | network and capture | scraper packet workflow |
| `41_private_mode_userdir.py` | attach and operational flows | private mode vs `user_dir` |
| `42_xpath_picker_complex_showcase.py` | iframe shadow xpath | picker showcase |
| `43_zhipin_xpath_picker.py` | iframe shadow xpath | real-site picker workflow |
| `44_shopee_userdir_xpath.py` | iframe shadow xpath | real-site persistent-profile picker workflow |
| `45_js_setter_untrusted_input.py` | advanced bidi and trusted events | `isTrusted` and JS event behavior |

## Companion Areas

- use `standards/` when the example depends on protocol-level event or command semantics
- use `references/fingerprint-browser-guide.md` when the workflow is high-risk, profile-sensitive, or fingerprint-sensitive
