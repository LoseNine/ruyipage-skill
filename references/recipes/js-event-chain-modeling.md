# JS Event Chain Modeling

## Use This Recipe When

- the task needs JS-driven interaction rather than only native pointer or keyboard actions
- the target control reacts to a specific event sequence
- the user explicitly asks about `ruyi: true`, `isTrusted`, or human-like JS event simulation
- a partial JS setter or one-shot event dispatch is not enough

## Core Principle

In `ruyiPage`, a `run_js` route with `ruyi: true` should be treated as a first-class high-fidelity path when the interaction is modeled completely.

The real quality boundary is not:

- JS versus BiDi

The real quality boundary is:

- incomplete event simulation versus complete event-chain modeling

## Recommended Example Path

1. `07_javascript.py`
2. `29_script_input_advanced.py`
3. `45_js_setter_untrusted_input.py`
4. `20_advanced_input.py` for comparison against native action routes

## Default Modeling Strategy

1. Identify the actual control type.
2. Determine which browser-visible state changes the control expects.
3. Identify the full event sequence required by that control.
4. Use `run_js` to update state and dispatch the full event chain.
5. Apply `ruyi: true` to the relevant event constructors.
6. Validate the result from the page's perspective rather than assuming the dispatch succeeded semantically.

## Control-Specific Thinking

### Text input

Possible concerns:

- focus state
- value mutation
- `beforeinput`
- `input`
- key-related events if the page listens to them
- `change` on blur or finalization

### Select control

Possible concerns:

- focus
- selection state change
- `input`
- `change`
- click or pointer-related events if the UI is custom rather than native

### Checkbox or radio

Possible concerns:

- checked-state mutation
- click semantics
- `input`
- `change`

### Custom component

Possible concerns:

- internal component state
- synthetic framework listeners
- pointer and keyboard events
- hidden input synchronization
- blur/focus transitions

## What The AI Should Explain

When proposing a JS route, the AI should name:

- the control type
- the expected state changes
- the likely event sequence
- where `ruyi: true` is important
- how the result will be validated

## Common Failure Modes

- setting a DOM property without dispatching follow-up events
- dispatching only `change` when the control actually depends on earlier events
- forgetting focus or blur transitions
- treating a custom widget like a plain native input
- using `ruyi: true` on one event while leaving the rest of the chain incomplete

## Decision Rule

Choose the route that best matches the target behavior:

- use element methods when the normal path already works
- use `page.actions` when native pointer or keyboard choreography is the right fit
- use `run_js` plus a complete `ruyi: true` event chain when the control's logic is better reproduced from the script side

## Validation Checklist

- did the visible UI state change correctly
- did the underlying form value actually change
- did framework listeners react
- did dependent requests or page updates fire
- did the site accept the interaction as if it were user-driven

## Related References

- `references/examples/04-javascript-and-script.md`
- `references/examples/03-interactions-and-actions.md`
- `references/examples/11-advanced-bidi-and-trusted-events.md`
- `references/api-decision-guide.md`
- `standards/modules/input.md`
- `standards/modules/script.md`
