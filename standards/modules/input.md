# Input Module

## Purpose

The `input` module covers action execution, action release, and file-setting behavior at the protocol layer.

## Why It Matters In `ruyiPage`

This module is the standard-side foundation for many interaction flows that appear in `page.actions` and related high-fidelity input behavior.

## Core Standard Areas

- `input.performActions`
- `input.releaseActions`
- `input.setFiles`
- file dialog related event surfaces

## Practical `ruyiPage` Alignment

Most relevant local examples:

- `05_actions_chain.py`
- `20_advanced_input.py`
- `23_download.py`
- `35_native_bidi_drag.py`
- `36_native_bidi_select.py`

## Important Modeling Note

The `input` module is not the only route to high-fidelity behavior in `ruyiPage`.

For some controls, `run_js` plus a complete event sequence with `ruyi: true` can achieve the same interaction tier as a BiDi-style native action path.

The important distinction is not:

- input module equals high fidelity
- JS equals lower fidelity

The important distinction is:

- whether the control's expected state transitions and event sequence are modeled completely

## AI Guidance

- prefer `page.actions` when native pointer, keyboard, drag, or file-setting semantics are the best fit
- prefer a JS event-chain route when the control logic is better reproduced from script and the full event chain can be modeled with `ruyi: true`
- explain the expected sequence, not only the chosen API surface

## Related References

- `references/recipes/js-event-chain-modeling.md`
- `references/examples/03-interactions-and-actions.md`
- `references/examples/11-advanced-bidi-and-trusted-events.md`
