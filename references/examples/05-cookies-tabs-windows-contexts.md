# Cookies Tabs Windows Contexts

## Goal

Use this topic when the task is about session state, multiple tabs, windows, user contexts, or browser-level isolation.

## Primary Examples

- `08_cookies.py`
- `09_tabs.py`
- `16_window_management.py`
- `25_browser_user_context.py`
- `26_browsing_context_advanced.py`
- `37_three_isolated_user_context_tabs.py`

## Supporting Examples

- `41_private_mode_userdir.py`

## Main Capabilities

- read, set, and delete cookies
- open and switch tabs
- manage windows and browser-visible state
- create and isolate user contexts
- structure multi-account flows safely

## Recommended Starting Point

Start with `08_cookies.py` for session state.

Use `09_tabs.py` for multi-page same-session workflows.

Use `25_browser_user_context.py` and `37_three_isolated_user_context_tabs.py` when isolation matters.

## When To Escalate

- move to `39_attach_exist_browser.py` when the browser session already exists
- move to `41_private_mode_userdir.py` when persistent profile behavior is part of the design

## Caveats

- tabs in one context do not provide the same isolation as separate user contexts
- cookie reuse alone may be insufficient for harder account-state workflows

## W3C BiDi Mapping

- strong alignment with `browser`, `browsingContext`, and `storage`
- user contexts are especially relevant to the `browser` module
