# Browser Module

## Purpose

The `browser` module covers browser-wide operations such as user contexts, client windows, and download behavior.

## Why It Matters In `ruyiPage`

It is the standard-side basis for user-context isolation, multi-account workflows, window state management, and browser-level download control.

## Core Standard Areas

- user context creation and removal
- listing user contexts
- client window discovery
- window state changes
- download behavior

## Practical `ruyiPage` Alignment

Most relevant local examples:

- `16_window_management.py`
- `23_download.py`
- `25_browser_user_context.py`
- `37_three_isolated_user_context_tabs.py`

## AI Guidance

- use the `browser` module to explain user-context and browser-level isolation semantics
- keep page-level automation separate from browser-level identity and window management concerns
