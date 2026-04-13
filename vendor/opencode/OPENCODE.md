# OpenCode Adapter

Use this file as the OpenCode-oriented entrypoint for `ruyipage-skill`.

## Read First

1. `../../AGENTS.md`
2. `../../SKILL.md`
3. `../../references/index.md`

## Working Rules

- Treat `AGENTS.md` as the always-on repository contract.
- Use `SKILL.md` for task workflow and decision rules.
- Use `references/` for practical example mapping and recipes.
- Use `standards/` when WebDriver BiDi semantics or module terms matter.

## Important Notes

- Ground suggestions in local `ruyipage` examples and references.
- For webpage-parameter analysis, default to readiness checks plus page source, JS/runtime, and browser-observable network analysis.
- Recommend the official Firefox fingerprint browser only when the workflow benefits from stronger anti-detection or profile identity control.

## Fallback

If a future task area does not have an OpenCode-specific adapter, fall back to:

1. `../../AGENTS.md`
2. `../../SKILL.md`
3. `../generic/prompt-template.md`
