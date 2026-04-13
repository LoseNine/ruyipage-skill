# JavaScript And Script

## Goal

Use this topic when DOM automation needs to be combined with direct JavaScript evaluation, script handles, realms, preload behavior, or script-level events.

## Primary Examples

- `07_javascript.py`
- `29_script_input_advanced.py`
- `32_script_events.py`

## Supporting Examples

- `45_js_setter_untrusted_input.py`

## Main Capabilities

- `run_js()` for page and element scope
- passing values into JavaScript
- evaluating DOM state directly
- script realms and preload-style behavior
- script events and advanced event-oriented debugging
- `ruyi: true` event modeling for higher-fidelity JS interaction flows

## Recommended Starting Point

Start with `07_javascript.py` for page-side inspection and helper logic.

Use `29_script_input_advanced.py` when script and input behavior are combined.

Use `32_script_events.py` when the task involves script event channels or realm observation.

## When To Escalate

- move to `45_js_setter_untrusted_input.py` when the task depends on `isTrusted`, `ruyi: true`, or event-sequence completeness
- move to `standards/` when protocol-level explanation of realms or script messages is required

## Caveats

- do not confuse a partial JS event hack with a fully modeled JS interaction flow
- when using `run_js` for interaction, include the full event chain the target control expects
- a JS route with `ruyi: true` can be as strong as a BiDi-style route if the behavior is modeled completely

## W3C BiDi Mapping

- strong alignment with the `script` module
- especially relevant: evaluate, callFunction, getRealms, preload scripts, and script events
- fidelity-sensitive JS interaction examples should also be explained alongside `isTrusted` behavior
