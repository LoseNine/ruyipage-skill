# Webpage Comprehensive Analysis

## Use This Recipe When

- the user asks to analyze webpage parameters
- the user wants to inspect request parameters, signatures, tokens, or payload structure
- the task requires a comprehensive view of page source, runtime clues, and browser-observable network traffic

## Default Rule

Do not analyze too early.

For this kind of task, the default flow is:

1. start listeners and collectors before navigation
2. navigate to the page
3. wait for the page to load
4. capture HTML, JS clues, and network traffic
5. analyze parameters only after the capture is complete enough to support a conclusion

## Recommended Example Path

1. `04_wait_conditions.py`
2. `24_navigation_events.py`
3. `07_javascript.py`
4. `31_network_events.py`
5. `28_network_data_collector.py`
6. `40_scraper_packet_capture.py`

## Required Capture Areas

### Page readiness

- `page.wait.doc_loaded(timeout=...)`
- `page.navigation.start()` plus `wait(...)` when event confirmation helps
- final `document.readyState`

### Page source

- `page.html`
- `document.documentElement.outerHTML` via `run_js`
- iframe-local HTML when relevant

### JS clues

- inline script contents when visible in DOM
- external script `src` URLs
- runtime config or globals exposed on `window`
- relevant values extracted through `run_js`

### Network traffic

- `page.events` for network event visibility
- `page.network.add_data_collector(...)` for request and response bodies
- `request_id` correlation across request and response data
- interception when request-level control or guaranteed request object capture is needed

## Recommended Workflow

### 1. Prepare capture before navigation

Start the relevant listeners before `page.get(url)` so the early requests are not missed.

Typical setup areas:

- `page.events`
- `page.network.add_data_collector(...)`
- `page.intercept` when request-level control is needed

### 2. Navigate and wait

Navigate first, then wait for readiness with explicit checks.

Preferred readiness order:

1. `page.wait.doc_loaded(...)`
2. `browsingContext.domContentLoaded` or `browsingContext.load` when event confirmation is useful
3. bounded extra stabilization only if the page is SPA-heavy or still issuing important async requests

Expected output for this step:

- final page URL
- title if available
- readiness evidence used for the analysis

### 3. Capture DOM and HTML

Capture at least:

- final `page.url`
- `page.title`
- `page.html`
- `document.documentElement.outerHTML`

If frames matter, inspect them separately instead of assuming the main page snapshot is enough.

Expected output for this step:

- page HTML snapshot
- rendered DOM snapshot details if relevant
- any frame-specific note if the content is not all in the main page

### 4. Capture JS runtime clues

Use `run_js` to inspect:

- script tags
- script URLs
- global config objects on `window`
- token, sign, timestamp, nonce, or trace-style values that already exist in runtime state

Expected output for this step:

- script clues
- runtime globals or config findings
- any value that appears relevant to parameters or request construction

### 5. Capture network data

For each important request, preserve as much of this as possible:

- `request_id`
- method
- URL
- headers
- request body
- response status
- response body

Expected output for this step:

- a request/response table or summary keyed by `request_id` when available
- the likely target requests rather than unrelated static assets

### 6. Continue briefly after document load

Many modern pages still issue meaningful async requests after the initial document load.

Keep the capture alive for a short bounded window after readiness if the page is still settling or if important requests are triggered just after load.

### 7. Produce a structured analysis

The final analysis should be organized into:

1. readiness evidence
2. page-source findings
3. JS/runtime findings
4. network findings
5. likely parameter sources and relationships
6. uncertainties or missing pieces

Do not stop at a vague summary. The result should make clear what evidence was collected and what conclusions actually follow from it.

## Important Distinctions

### `page.html` is not always the same as original response HTML

`page.html` is a rendered DOM snapshot. If the user cares about original server-returned HTML, that may need to be captured from the main document response body when available.

### "All network packets" should be interpreted carefully

In this skill, that means all browser-observable requests and responses after capture starts. It does not mean OS-level packet capture.

### Full JS understanding is a staged process

Start from:

- script tags
- runtime globals
- network-correlated values

Only escalate further when the simpler evidence is not enough.

## Common Failure Modes

- enabling capture after navigation and missing early requests
- analyzing before `doc_loaded`
- only checking DOM and missing the real parameters in network bodies
- ignoring iframe-local content
- stopping capture too early on SPA pages

## Related References

- `references/recipes/js-runtime-and-parameter-hunting.md`
- `references/web-analysis-checklist.md`
- `references/examples/04-javascript-and-script.md`
- `references/examples/07-network-and-packet-capture.md`
- `standards/modules/network.md`
- `standards/modules/script.md`
