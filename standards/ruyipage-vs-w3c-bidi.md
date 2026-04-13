# RuyiPage Vs W3C BiDi

`ruyiPage` should be understood as a practical automation framework that exposes user-facing workflows while also aligning with underlying WebDriver BiDi concepts.

## Mapping Principle

- `ruyiPage` APIs are the practical execution layer
- W3C BiDi modules are the protocol semantics layer

Both are useful, but they should not be conflated.

## Rough Mapping Examples

- `page.actions` relates strongly to the BiDi `input` module
- network interception and collectors relate to the BiDi `network` module
- `run_js`, realms, handles, and preload scripts relate to the BiDi `script` module
- tab, context, prompt, screenshot, print, and navigation behavior relate to `browsingContext`
- user contexts and browser-wide operations relate to `browser`
- cookies map conceptually to `storage`

## What `ruyiPage` Adds Above Raw BiDi

- higher-level page and element abstractions
- example-driven workflows for scraping and packet capture
- XPath picker support and real-site oriented traversal assistance
- convenience methods and workflow grouping that are friendlier than raw protocol messages
- integration guidance around existing browser attach and operational Firefox usage

## What An AI Should Do

- explain the `ruyiPage` API the user actually writes
- mention the BiDi module when it helps explain semantics or boundaries
- avoid dropping down to raw protocol vocabulary unless the task explicitly needs that level
