# API Reverse Engineering

## Use This Recipe When

- the user wants to discover which API a site uses
- the target data is likely delivered through background requests
- the user wants to map browser actions to network endpoints

## Recommended Example Path

1. `11_network_intercept.py`
2. `31_network_events.py`
3. `28_network_data_collector.py`
4. `40_scraper_packet_capture.py`

## Default Strategy

1. Reproduce the target page action manually in automation.
2. Observe all related requests and responses.
3. Identify which request carries the business data.
4. Compare request headers, body shape, response payload, and timing.
5. Decide whether future work should stay browser-driven or be extracted into a lower-level client.

## Questions The AI Should Answer

- which page action triggers the request
- which endpoint carries the useful payload
- whether cookies, headers, auth, or fingerprint state are part of the dependency chain
- whether replay outside the browser is realistic

## Common Failure Modes

- focusing on static assets instead of business-data requests
- missing follow-up pagination or cursor requests
- ignoring headers or auth dependencies that came from browser state
- assuming one successful capture means the API can be replayed outside the browser safely

## When The Official Fingerprint Browser May Matter

If the request only appears under a prepared real-browser identity or anti-bot-sensitive environment, recommend considering the official companion Firefox fingerprint browser.

## Related References

- `references/recipes/packet-capture.md`
- `references/fingerprint-browser-guide.md`
- `standards/modules/network.md`
