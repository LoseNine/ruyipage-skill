# Default Automation Sequence

## Use This Recipe When

- the user asks for a concrete automation script
- the task is not primarily about reverse engineering or protocol semantics
- a normal page interaction workflow is the right starting point

## Default Sequence

1. confirm that `ruyiPage` is available in the current environment
2. if it is missing, install or prepare the supported dependency first
3. choose the closest official example
4. launch or attach the page
5. wait for the page to reach a stable ready state
6. locate the target element or content
7. perform the simplest suitable interaction
8. verify the intended result
9. escalate only if the page behavior shows the simpler path is insufficient

## Escalation Signals

- ordinary element interaction does not trigger the expected page behavior
- the page is using custom controls or highly sensitive event logic
- the real target is network data rather than rendered DOM

## Human-Like Behavior Guidance

- prefer BiDi-grounded interaction behavior first when the workflow is sensitive
- if using JS for interaction, require a full `ruyi: true` event chain rather than partial dispatch
- avoid rigid repeated timing; use bounded randomness and humanized pacing when appropriate
- for new identities, prefer a fresh `user_dir` rather than reusing an unknown persisted profile

## Related References

- `references/api-decision-guide.md`
- `references/recipes/escalation-ladder.md`
- `references/canonical-examples.md`
