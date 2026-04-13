# Compatibility

This repository is designed to work well across many AI coding tools, not only one specific skill system.

## Source Of Truth

The canonical content lives in plain Markdown files:

- `AGENTS.md`
- `SKILL.md`
- `references/`
- `standards/`

Tool-specific files are adapters, not the authoritative knowledge base.

## Supported Usage Model

This repository is intended to work in four ways:

1. direct repo-aware reading
   - tools read `AGENTS.md`, `README.md`, and linked references
2. skill-style loading
   - tools read `SKILL.md` as an explicit task skill
3. prompt injection by humans
   - users can paste or reference `vendor/generic/prompt-template.md`
4. vendor adapter mode
   - tool-specific entry files under `vendor/` point back to shared docs

## Compatibility Principles

- Keep root instructions short and stable.
- Keep detailed knowledge in linked Markdown references.
- Avoid duplicating core content per vendor.
- Prefer progressive disclosure over one giant instruction file.
- Use examples as the practical layer and standards as the semantic layer.

## Recommended Load Order For Any Tool

1. `AGENTS.md`
2. `SKILL.md`
3. `references/index.md`
4. `references/canonical-examples.md`
5. `references/api-decision-guide.md`
6. `standards/index.md` when BiDi semantics matter

## Vendor Adapters

See `vendor/` for thin tool-oriented entry files.

Those files should remain minimal and should point back to shared documents instead of reimplementing them.

Current adapters include:

- `vendor/opencode/OPENCODE.md`
- `vendor/claude/CLAUDE.md`
- `vendor/cursor/cursor-rules.md`
- `vendor/windsurf/rules.md`
- `vendor/cline/system-prompt.md`
- `vendor/generic/prompt-template.md`

If a tool does not have a dedicated adapter yet, use the generic fallback path:

1. `AGENTS.md`
2. `SKILL.md`
3. `vendor/generic/prompt-template.md`
