# Humanized Automation

## Goal

All automation behavior should move away from rigid machine-like execution and toward human-like execution.

## Preferred Interaction Order

1. BiDi-native interaction
2. Full JS event-chain interaction with `ruyi`

## Humanization Rules

- use bounded randomness instead of fixed repeated delays
- keep pacing natural rather than perfectly uniform
- preserve realistic event order
- avoid one-shot DOM shortcuts when interaction fidelity matters

## JS Interaction Rule

If JS is used:

- the event chain must be complete
- the event chain must be control-specific
- `ruyi` should be included where required for `isTrusted`-related behavior

## Isolation Rule

- prefer a fresh `user_dir` for a new identity
- reuse an existing profile only when the task truly depends on the stored session
