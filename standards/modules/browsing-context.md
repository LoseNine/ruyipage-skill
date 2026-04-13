# Browsing Context Module

## Purpose

The `browsingContext` module covers navigation, screenshots, prompts, context trees, viewport settings, printing, history traversal, and many important browser events.

## Why It Matters In `ruyiPage`

This module maps closely to what users think of as page and tab behavior, especially for navigation reasoning, screenshots, prompts, and context lifecycle.

## Core Standard Areas

- context creation and closing
- tree retrieval
- navigation and reload
- prompt handling
- screenshots and print
- viewport and history traversal
- navigation and lifecycle events

## Practical `ruyiPage` Alignment

Most relevant local examples:

- `01_basic_navigation.py`
- `06_screenshot.py`
- `17_user_prompts.py`
- `19_pdf_printing.py`
- `24_navigation_events.py`
- `26_browsing_context_advanced.py`
- `30_browsing_context_events.py`

## AI Guidance

- explain page-level operations in user terms first
- use `browsingContext` terminology when protocol precision matters
- distinguish between ordinary page operations and event-stream level reasoning
