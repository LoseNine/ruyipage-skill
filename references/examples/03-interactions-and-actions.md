# Interactions And Actions

## Goal

Use this topic when the main task is clicking, typing, clearing, dragging, hovering, using combo keys, or reproducing more realistic input behavior.

## Primary Examples

- `03_element_interaction.py`
- `05_actions_chain.py`
- `20_advanced_input.py`

## Supporting Examples

- `17_user_prompts.py`

## Main Capabilities

- simple element click and input
- action-chain based keyboard and mouse sequences
- drag, drop, hover, right-click, double-click, middle-click
- combo keys and humanized input
- prompt handling and interaction-sensitive workflows

## Recommended Starting Point

Start with `03_element_interaction.py` when the page accepts ordinary interactions.

Move to `05_actions_chain.py` when the workflow depends on key combos or ordered pointer actions.

Use `20_advanced_input.py` when trusted-like or higher-fidelity behavior matters.

Note that this is not the only high-fidelity route. A JS implementation that emits the full required event sequence with `ruyi: true` can also reach the same interaction tier.

## When To Escalate

- move to `35_native_bidi_drag.py` or `36_native_bidi_select.py` when native event fidelity is the problem
- move to `45_js_setter_untrusted_input.py` when the user explicitly asks about `isTrusted`, `ruyi: true`, or JS-driven realistic behavior

## Caveats

- interaction-sensitive pages often fail because of event fidelity, not locator quality
- if using JS for interaction, model the full control-specific event sequence instead of only one final event

## W3C BiDi Mapping

- strong alignment with the `input` module
- prompts align with `browsingContext.handleUserPrompt` and related events
