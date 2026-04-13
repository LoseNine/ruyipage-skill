# Script Module

## Purpose

The `script` module covers evaluation, function calls, handles, realms, preload scripts, and script-related events.

## Why It Matters In `ruyiPage`

It underlies much of the practical `run_js`, realm inspection, preload behavior, and advanced script-event functionality that appears in the local examples.

## Core Standard Areas

- `script.evaluate`
- `script.callFunction`
- `script.getRealms`
- `script.addPreloadScript`
- `script.removePreloadScript`
- `script.disown`
- script events such as `script.message`, `script.realmCreated`, `script.realmDestroyed`

## Practical `ruyiPage` Alignment

Most relevant local examples:

- `07_javascript.py`
- `29_script_input_advanced.py`
- `32_script_events.py`
- `45_js_setter_untrusted_input.py`

## AI Guidance

- keep the explanation grounded in `run_js` and user-visible behavior first
- mention realms, preload scripts, and events only when they improve precision
- distinguish between practical DOM scripting and protocol-level script semantics
