# Default Automation Sequence

## Use This Recipe When

- the user asks for a concrete automation script
- the task is not primarily about reverse engineering or protocol semantics
- a normal page interaction workflow is the right starting point

## Default Sequence

1. choose the closest official example
2. launch or attach the page
3. wait for the page to reach a stable ready state
4. locate the target element or content
5. perform the simplest suitable interaction
6. verify the intended result
7. escalate only if the page behavior shows the simpler path is insufficient

## Escalation Signals

- ordinary element interaction does not trigger the expected page behavior
- the page is using custom controls or highly sensitive event logic
- the real target is network data rather than rendered DOM

## Related References

- `references/api-decision-guide.md`
- `references/recipes/escalation-ladder.md`
- `references/canonical-examples.md`
