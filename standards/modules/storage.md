# Storage Module

## Purpose

The `storage` module covers cookie-oriented operations.

## Why It Matters In `ruyiPage`

It is the standard-side basis for cookie reading, writing, and deletion in session-oriented automation flows.

## Core Standard Areas

- `storage.getCookies`
- `storage.setCookie`
- `storage.deleteCookies`

## Practical `ruyiPage` Alignment

Most relevant local examples:

- `08_cookies.py`
- `41_private_mode_userdir.py`

## AI Guidance

- use `storage` terminology when precision helps explain cookie persistence or deletion behavior
- distinguish simple cookie reuse from stronger profile-level identity reuse
