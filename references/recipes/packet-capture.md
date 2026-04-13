# Packet Capture

## Use This Recipe When

- the user wants request or response data rather than only page text
- the task is scraping, API discovery, or reverse engineering
- the workflow depends on correlating browser actions with network traffic

## Recommended Example Path

1. `11_network_intercept.py`
2. `28_network_data_collector.py`
3. `40_scraper_packet_capture.py`
4. `31_network_events.py` when timing matters

## Default Strategy

1. Identify the user action that triggers the target request.
2. Use collectors or interception before performing that action.
3. Trigger the page interaction.
4. Capture and correlate request and response payloads.
5. Decide whether the task needs observation only or in-flight mutation.

## Choose The Right Layer

- use interception when the traffic must be controlled, mocked, or failed
- use collectors when the real goal is payload extraction
- use events when sequencing and timing are the real problem

## Common Failure Modes

- the wrong request was captured because the trigger action was unclear
- the target data lives in a later response rather than the first request
- the page action fires multiple related requests and correlation is missing
- the user is trying to scrape rendered DOM when the real data is only in network traffic

## Related References

- `references/examples/07-network-and-packet-capture.md`
- `standards/modules/network.md`
