# Advanced BiDi And Trusted Events

## Goal

Use this topic when the task is explicitly about event streams, native drag/select fidelity, trusted behavior, `ruyi: true` JS event modeling, or protocol-oriented Firefox automation details.

## Primary Examples

- `24_navigation_events.py`
- `30_browsing_context_events.py`
- `35_native_bidi_drag.py`
- `36_native_bidi_select.py`
- `45_js_setter_untrusted_input.py`

## Supporting Examples

- `33_log_input_events.py`

## Main Capabilities

- observe event streams instead of relying only on blocking calls
- reason about navigation and context lifecycle events
- diagnose native drag and select behavior
- explain why `isTrusted` and realistic event generation can matter
- explain how `run_js` plus a complete `ruyi: true` event chain can match high-fidelity interaction goals
- connect user-facing automation behavior to lower-level BiDi semantics

## Recommended Starting Point

Start with `24_navigation_events.py` when the problem is navigation sequencing.

Use `30_browsing_context_events.py` when context lifecycle matters.

Use `35_native_bidi_drag.py`, `36_native_bidi_select.py`, and `45_js_setter_untrusted_input.py` when fidelity is the actual issue.

## When To Escalate

- move to `standards/` when a protocol-accurate explanation is required
- combine with network or script event examples when the debugging surface spans multiple modules

## Caveats

- these are advanced references, not the default starting point for ordinary automation
- AI should explain why it is escalating to this layer instead of assuming it is always necessary
- when recommending a JS route, explicitly describe the event sequence that must be completed with `ruyi: true`

## W3C BiDi Mapping

- strong alignment with `browsingContext`, `input`, and `script`
- event-stream reasoning should be explained in terms of subscriptions and module events when helpful
