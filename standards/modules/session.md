# Session Module

## Purpose

The `session` module covers session lifecycle and event subscription control.

## Why It Matters In `ruyiPage`

It provides the protocol-level basis for starting a BiDi session, checking status, and subscribing to event streams that power higher-level features such as `page.events`, `page.navigation`, and other event-oriented helpers.

## Core Standard Areas

- `session.status`
- `session.new`
- `session.end`
- `session.subscribe`
- `session.unsubscribe`

## Practical `ruyiPage` Alignment

Most relevant local examples:

- `24_navigation_events.py`
- `30_browsing_context_events.py`
- `31_network_events.py`
- `32_script_events.py`

## AI Guidance

- use session terminology when explaining why event listeners must be started before the browser emits the events
- keep the user-facing explanation centered on `ruyiPage` helpers rather than raw protocol messages unless protocol precision is needed
