# Windsurf Adapter

This adapter points Windsurf-style agents to the shared knowledge base.

## Read In Order

1. `../../AGENTS.md`
2. `../../SKILL.md`
3. `../../references/index.md`

## Working Rules

- Ground every solution in local `ruyipage` examples when possible.
- Distinguish user-facing `ruyiPage` APIs from lower-level WebDriver BiDi concepts.
- Escalate to interception, BiDi, or fingerprint-browser workflows only when the task requires them.
