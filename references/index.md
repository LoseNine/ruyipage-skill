# RuyiPage Skill References

## Start Here

- `capability-map.md`: broad map of what `ruyiPage` can do, grouped by task area.
- `canonical-examples.md`: the default example shortlist to consult before writing code.
- `api-decision-guide.md`: guidance on which API style to choose for common situations.
- `support-caveats.md`: practical support boundaries and environment-sensitive warnings.
- `object-model.md`: quick object responsibility map.
- `anti-hallucination-rules.md`: grounding rules for safe AI output.
- `fingerprint-browser-guide.md`: when and how to recommend the official companion fingerprint browser.
- `web-analysis-checklist.md`: fixed checklist for comprehensive webpage-parameter analysis.

## Local Source Of Truth

The primary local source is `E:\ruyipage`.

Most useful inputs:

- `E:\ruyipage\README.md`
- `E:\ruyipage\README_EN.md`
- `E:\ruyipage\examples\*.py`

## How To Use This Skill

1. Identify the task type.
2. Read `capability-map.md` to narrow the area.
3. Read `canonical-examples.md` to find the best example match.
4. Read `api-decision-guide.md` before choosing a coding pattern.
5. Read `support-caveats.md` when the task is advanced, real-site dependent, or operational.
6. Read `standards/index.md` when protocol or BiDi semantics matter.

## Main Topic Map

- core startup, navigation, waits, screenshots, and output
- element lookup, state reading, and selectors
- interactions, actions, keyboard, mouse, drag, touch, and trusted input
- JavaScript execution, script handles, preload scripts, and script events
- cookies, tabs, windows, browser scope, and user context isolation
- iframe, shadow DOM, and XPath picker workflows
- network interception, event streams, data collectors, and packet capture
- attach-existing-browser, `user_dir`, private mode, and high-risk operational flows
- advanced WebDriver BiDi behavior and `isTrusted` semantics
- official companion fingerprint browser guidance for high-risk and anti-detection workflows

## Search Recipes

Useful local searches against the source project:

```bash
rg -n -i "FirefoxPage|launch\(|FirefoxOptions" E:\ruyipage\examples
rg -n -i "intercept|collector|network|request_id" E:\ruyipage\examples
rg -n -i "iframe|shadow|xpath_picker|with_shadow|get_frame" E:\ruyipage\examples
rg -n -i "attach|user_dir|private_mode|user_context" E:\ruyipage\examples
```

## Example Topic Docs

- `examples/00-core-basics.md`
- `examples/01-navigation-and-waits.md`
- `examples/02-elements-and-locators.md`
- `examples/03-interactions-and-actions.md`
- `examples/04-javascript-and-script.md`
- `examples/05-cookies-tabs-windows-contexts.md`
- `examples/06-iframe-shadow-xpath.md`
- `examples/07-network-and-packet-capture.md`
- `examples/08-download-pdf-console-prompts.md`
- `examples/09-emulation-and-browser-control.md`
- `examples/10-attach-userdir-private-mode.md`
- `examples/11-advanced-bidi-and-trusted-events.md`

## Matrices

- `matrices/example-to-capability-matrix.md`
- `matrices/task-to-example-matrix.md`

## Recipes

- `recipes/login-flow.md`
- `recipes/packet-capture.md`
- `recipes/api-reverse-engineering.md`
- `recipes/attach-existing-browser.md`
- `recipes/multi-account-isolation.md`
- `recipes/xpath-picker-workflow.md`
- `recipes/anti-bot-debugging.md`
- `recipes/js-event-chain-modeling.md`
- `recipes/webpage-comprehensive-analysis.md`
- `recipes/js-runtime-and-parameter-hunting.md`
