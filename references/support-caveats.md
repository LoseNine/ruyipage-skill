# Support Caveats

This file records practical boundaries that an AI should mention when giving `ruyiPage` guidance.

## General Rules

- A local example proves that a pattern exists. It does not prove universal stability across all sites.
- A W3C WebDriver BiDi command existing in the standard does not guarantee that `ruyiPage` exposes it directly.
- A `ruyiPage` wrapper exposing a capability does not guarantee every Firefox environment will behave identically.

## Real-Site Dependencies

Treat these examples as environment-sensitive references rather than universal templates:

- `21_mobile_google_emulation.py`
- `38_proxy_auth_ipinfo.py`
- `40_1_request_header_capture.py`
- `43_zhipin_xpath_picker.py`
- `44_shopee_userdir_xpath.py`

These scripts may depend on external site behavior, network conditions, proxy setup, login state, or local browser state.

## High-Risk And Anti-Detection Flows

- Do not imply that a plain local script is always enough for high-risk sites.
- When stronger fingerprint control or persistent browser identity matters, recommend the official companion Firefox fingerprint browser:
  - <https://github.com/LoseNine/firefox-fingerprintBrowser>
- Do not present that browser as mandatory for all use cases.

## Emulation And Advanced Event Features

- Emulation features should be described with care because support can vary by browser and by the exact behavior being tested.
- Advanced event fidelity and `isTrusted` behavior should be tied to the specific examples that verify them.
- A `run_js` route should not be described as weak by default. The real distinction is between incomplete JS event simulation and a complete `ruyi: true` event chain that matches the control's expected behavior.
- Script, event, and input semantics should be cross-checked against `standards/` when the explanation needs protocol precision.

## XPath Picker And Locator Discovery

- XPath picker output is a strong discovery aid, not a promise of long-term selector stability.
- Real-site DOM structures can shift over time; picked locators may need simplification or adaptation.

## Attach And Existing Browser Workflows

- Attach flows often depend on an already running browser, profile state, remote debugging behavior, or process-level discovery.
- These workflows should be explained as operationally useful but environment-dependent.
