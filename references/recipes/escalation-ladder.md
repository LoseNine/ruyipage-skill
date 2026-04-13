# Escalation Ladder

## Purpose

Use this recipe when a simpler supported path is not enough and a more advanced supported path is needed.

## Level 1: page and element APIs

Best for:

- standard DOM interactions
- simple extraction, clicks, inputs, waits, and verification

Move on when:

- the page reacts incorrectly despite apparently correct interaction

## Level 2: `page.actions`

Best for:

- drag, hover, combo keys, pointer choreography, and native-like interaction sequencing

Move on when:

- the control logic is better represented as a JS-side event chain than as pointer motion

## Level 3: `run_js` plus full `ruyi: true` event chain

Best for:

- event-sensitive custom controls
- JS-centric form or component behavior
- cases where a complete control-specific event sequence matters

Move on when:

- the unresolved question is really about network payloads or hidden request flow

## Level 4: interception, collectors, and event streams

Best for:

- packet capture
- parameter origin analysis
- scraper diagnostics
- request and response correlation

Move on when:

- the explanation must use protocol-level module or event semantics

## Level 5: BiDi semantics and standards layer

Best for:

- protocol-accurate explanation
- event and module terminology
- clarifying how `ruyiPage` behavior maps to WebDriver BiDi

## Rule

Always choose the smallest supported level that solves the problem reliably.
