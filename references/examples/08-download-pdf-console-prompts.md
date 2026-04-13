# Download PDF Console Prompts

## Goal

Use this topic when the task is about supporting browser-side workflows beyond ordinary page interaction, such as downloads, PDF output, console logs, or dialogs.

## Primary Examples

- `12_console_listener.py`
- `17_user_prompts.py`
- `19_pdf_printing.py`
- `23_download.py`

## Supporting Examples

- `33_log_input_events.py`
- `34_remaining_commands.py`

## Main Capabilities

- listen to console output
- handle prompts, alerts, and login dialogs
- create PDF output
- manage download behavior and file retrieval flow
- inspect less common command surfaces

## Recommended Starting Point

Start with `12_console_listener.py` for page observability.

Use `17_user_prompts.py` when dialog handling is part of the flow.

Use `23_download.py` for file download workflows.

## When To Escalate

- move to event-oriented references when download or prompt behavior needs event-level reasoning
- use `34_remaining_commands.py` as a coverage appendix, not a first learning path

## Caveats

- some of these flows depend strongly on browser behavior and timing
- `34_remaining_commands.py` is better treated as a surface-area reminder than a primary tutorial

## W3C BiDi Mapping

- console aligns with `log`
- prompt handling aligns with `browsingContext`
- download behavior aligns with `browser` and `browsingContext` related areas
