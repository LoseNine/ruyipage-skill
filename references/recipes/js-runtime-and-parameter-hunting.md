# JS Runtime And Parameter Hunting

## Use This Recipe When

- the user believes parameters are generated in page JavaScript
- the request includes sign, token, nonce, timestamp, or trace-like values
- DOM analysis alone is not enough to explain where parameters come from

## Goal

Find parameter clues that exist in page runtime state and connect them to the network requests that use them.

## Recommended Example Path

1. `07_javascript.py`
2. `29_script_input_advanced.py`
3. `32_script_events.py`
4. `28_network_data_collector.py`
5. `40_scraper_packet_capture.py`

## Default Strategy

1. Wait for page readiness first.
2. Capture the relevant network requests.
3. Inspect DOM-visible scripts and runtime globals.
4. Compare runtime values against request parameters and headers.
5. Narrow down which values are static, session-bound, time-based, or user-action-derived.

## What To Inspect First

### DOM-visible scripts

Use `run_js` or page inspection to identify:

- inline scripts
- external script URLs
- embedded configuration blobs in script tags

### Runtime globals

Use `run_js` to inspect likely `window` properties that may expose:

- app config
- API base URLs
- csrf or token values
- user or session markers
- timestamp or sign helpers already attached to runtime objects

### Network-correlated values

Compare runtime findings with:

- query parameters
- request body fields
- dynamic headers
- cookies if relevant

## Practical Heuristics

- if a value appears in both `window` config and request headers, capture both and record the relationship
- if a parameter changes every request, compare time-based or nonce-like runtime values
- if a parameter appears only after a click or input, inspect runtime state again after the triggering action

## Common Failure Modes

- trying to explain a parameter before confirming which request is the real target
- looking only at HTML and ignoring runtime globals
- looking only at JS values without comparing them to request bodies and headers
- failing to re-check runtime state after the user action that triggers the request

## Related References

- `references/recipes/webpage-comprehensive-analysis.md`
- `references/examples/04-javascript-and-script.md`
- `references/examples/07-network-and-packet-capture.md`
- `standards/modules/script.md`
- `standards/modules/network.md`
