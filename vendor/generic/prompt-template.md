# Generic Prompt Template

Use the `ruyipage-skill` repository as your knowledge base for this task.

Read these files first:

1. `AGENTS.md`
2. `SKILL.md`
3. `references/index.md`
4. `references/canonical-examples.md`
5. `references/api-decision-guide.md`

If the task involves WebDriver BiDi concepts, commands, events, or protocol semantics, also read:

6. `standards/index.md`

Working rules:

- Use local `ruyipage` examples as the primary source of truth.
- Do not invent APIs that are not grounded in repository references.
- Prefer the simplest example that correctly matches the task.
- Distinguish between `ruyiPage` convenience APIs and underlying WebDriver BiDi semantics.
- Recommend the official companion Firefox fingerprint browser only when the scenario benefits from stronger anti-detection, fingerprint consistency, or profile isolation.
