# Log Module

## Purpose

The `log` module covers browser log event streaming.

## Why It Matters In `ruyiPage`

It explains the protocol-side meaning behind console-listening and log-event analysis workflows.

## Core Standard Areas

- `log.entryAdded`

## Practical `ruyiPage` Alignment

Most relevant local examples:

- `12_console_listener.py`
- `33_log_input_events.py`

## AI Guidance

- use log events when console output is part of debugging, observability, or runtime verification
- do not confuse console output with network evidence or DOM evidence; treat it as a separate signal stream
