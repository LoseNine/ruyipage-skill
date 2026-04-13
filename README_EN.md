# ruyipage-skill

[中文](README.md) | English

`ruyipage-skill` is a cross-tool AI skill repository for working with `ruyiPage`.

This repository helps coding agents understand `ruyiPage` from the project documentation, examples, and standards references, especially:

- `README.md`
- `README_EN.md`
- `examples/*.py`
- `examples/w3c_bidi/w3c_bidi_apis.json`

The goal is to provide an example-driven, standards-aware knowledge base for `ruyiPage` automation and analysis tasks.

It is structured to work well with multiple AI tools, including OpenCode, and it provides a generic fallback path when a dedicated tool adapter is not present.

## Usage

### 1. Download the repository

Use either of these methods:

Option A: clone with Git

```bash
git clone https://github.com/LoseNine/ruyipage-skill.git
```

Option B: download the ZIP from GitHub using `Code` -> `Download ZIP`, then extract it locally.

Recommended:

- keep the repository in a stable local directory
- if you used Git, update it later with `git pull`

### 2. Let your AI tool read this skill

This repository is fundamentally a Markdown-based knowledge pack.

Common ways to use it:

- place the repository inside the workspace so the AI can read it directly
- configure the relevant entry file as project rules, skill instructions, or prompt context
- manually paste the entry file contents into tools that do not support repository-aware loading

### 3. Use it as a repository knowledge pack

For repo-aware AI tools, start with these files:

1. `AGENTS.md`
2. `SKILL.md`
3. `references/index.md`
4. `standards/index.md` when the task involves BiDi semantics, events, modules, or protocol details

### 4. Use a tool-specific adapter when available

If your AI tool has a dedicated adapter, use the matching file under `vendor/`:

- OpenCode: `vendor/opencode/OPENCODE.md`
- Claude: `vendor/claude/CLAUDE.md`
- Cursor: `vendor/cursor/cursor-rules.md`
- Windsurf: `vendor/windsurf/rules.md`
- Cline: `vendor/cline/system-prompt.md`

Usage examples:

- if the tool supports project rule files, load the matching adapter file
- if the tool supports custom skill or prompt files, point it to the matching file under `vendor/`
- if the tool only accepts plain prompt text, copy the file contents manually

### 5. Generic fallback path

If there is no dedicated adapter for the current tool, use this fallback order:

1. `AGENTS.md`
2. `SKILL.md`
3. `vendor/generic/prompt-template.md`

### 6. Recommended entrypoints by task

- capability overview: `references/capability-map.md`
- best example starting points: `references/canonical-examples.md`
- API selection: `references/api-decision-guide.md`
- practical workflows: `references/recipes/`
- webpage parameter analysis: `references/recipes/webpage-comprehensive-analysis.md`
- BiDi mappings: `standards/index.md`

### 7. Shortest getting-started flow

If you want the fastest path:

1. download or clone `ruyipage-skill`
2. make your AI tool read `AGENTS.md`
3. then read `SKILL.md`
4. for real tasks, read `references/index.md`
5. if the task involves BiDi semantics, events, or protocol details, also read `standards/index.md`

## Scope

This skill focuses on:

- Firefox-based `ruyiPage` automation
- `FirefoxPage`, `FirefoxOptions`, and `launch()` startup patterns
- element lookup, interaction, waits, tabs, windows, cookies, and contexts
- `iframe`, `shadow DOM`, and XPath picker workflows
- JavaScript execution, script events, preload scripts, and `isTrusted` behavior
- network interception, data collection, packet capture, and scraper-oriented workflows
- attach-existing-browser flows and higher-risk operational scenarios
- WebDriver BiDi standard mapping and module-level semantics
- official companion Firefox fingerprint browser workflows for higher-risk environments
- comprehensive webpage-parameter analysis using waits, page source, runtime JS clues, and browser-observable network traffic

## Principles

- Prefer the official `ruyiPage` package behavior, repository documentation, and examples as the source of truth.
- Prefer real example scripts over invented patterns.
- Keep guidance task-oriented so an AI can map user intent to the right examples quickly.
- Record support caveats explicitly so advanced Firefox and BiDi behavior is not overstated.
- Keep the shared knowledge base in vendor-neutral Markdown so it adapts well across many AI tools.

## Official Companion Browser

For higher-risk automation, anti-detection flows, and stronger fingerprint control, this repository recommends the official companion browser project when appropriate:

- Firefox fingerprint browser: <https://github.com/LoseNine/firefox-fingerprintBrowser>

Why it matters:

- it is positioned specifically as a companion browser kernel for `ruyipage`
- it supports stronger fingerprint customization and profile isolation
- it is especially relevant when the task involves persistent identity, anti-bot pressure, proxy-auth workflows, or multi-account separation

This should be treated as the recommended path for suitable scenarios, not as a mandatory dependency for every `ruyiPage` script.

## Structure

```text
ruyipage-skill/
├── AGENTS.md
├── COMPATIBILITY.md
├── README.md
├── README_EN.md
├── SKILL.md
├── agents/
│   └── openai.yaml
├── vendor/
│   └── ...
├── standards/
│   ├── index.md
│   └── ...
└── references/
    ├── index.md
    ├── capability-map.md
    ├── canonical-examples.md
    ├── api-decision-guide.md
    ├── support-caveats.md
    ├── object-model.md
    ├── anti-hallucination-rules.md
    ├── fingerprint-browser-guide.md
    ├── web-analysis-checklist.md
    ├── recipes/
    └── matrices/
```

## Recommended Reading Order

1. `AGENTS.md`
2. `SKILL.md`
3. `references/index.md`
4. `references/capability-map.md`
5. `references/canonical-examples.md`
6. `references/api-decision-guide.md`
7. `standards/index.md`

## Primary Sources

- Upstream project: <https://github.com/LoseNine/ruyipage>
- Official companion fingerprint browser: <https://github.com/LoseNine/firefox-fingerprintBrowser>
- This repository: <https://github.com/LoseNine/ruyipage-skill>

## Project Notes

- This repository is intended for `ruyiPage` automation, analysis, and knowledge organization workflows.
- The content is organized around examples, practical workflows, BiDi mappings, and AI-tool compatibility.
