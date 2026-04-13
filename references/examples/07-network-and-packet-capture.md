# Network And Packet Capture

## Goal

Use this topic when the real task is understanding browser traffic, intercepting requests, collecting response payloads, or building network-backed scraping workflows.

## Primary Examples

- `11_network_intercept.py`
- `18_advanced_network.py`
- `28_network_data_collector.py`
- `31_network_events.py`
- `40_scraper_packet_capture.py`

## Supporting Examples

- `23_download.py`
- `40_1_request_header_capture.py`

## Main Capabilities

- intercept requests and responses
- continue, fail, mock, and auth-handle traffic
- collect request and response bodies
- correlate packets with browser actions
- build scraper workflows around network truth rather than rendered HTML

## Recommended Starting Point

Start with `11_network_intercept.py` for basic interception.

Use `18_advanced_network.py` when traffic must be modified or controlled.

Use `28_network_data_collector.py` and `40_scraper_packet_capture.py` when payload capture is the main goal.

## When To Escalate

- move to `31_network_events.py` when event order and timing matter
- move to `40_1_request_header_capture.py` only when a real-site header workflow is truly relevant

## Caveats

- many scraping problems are easier to solve at the network layer than at the DOM layer
- real-site network examples are more environment-sensitive than local showcase examples

## W3C BiDi Mapping

- strong alignment with the `network` module
- especially relevant: intercepts, data collectors, request/response events, auth handling
