# ruyipage-skill

中文 | [English](README_EN.md)

`ruyipage-skill` is a self-maintained, cross-tool AI skill repository for working with `ruyiPage` locally.

This repository is designed to help coding agents understand `ruyiPage` through the project documentation, examples, and standards references, especially:

- `README.md`
- `README_EN.md`
- `examples/*.py`
- `examples/w3c_bidi/w3c_bidi_apis.json`

The goal is not to mirror a third-party skill repository. The goal is to maintain a local, example-driven and standards-aware knowledge base that stays aligned with your own `ruyipage` source tree.

It is structured to work well with multiple AI tools, including OpenCode, and to provide a generic fallback path when a tool-specific adapter is not present.

## Scope

This skill focuses on:

- Firefox-based `ruyiPage` automation
- `FirefoxPage`, `FirefoxOptions`, and `launch()` startup patterns
- element lookup, interaction, waits, tabs, windows, cookies, and contexts
- `iframe`, `shadow DOM`, and XPath picker workflows
- JavaScript execution, script events, preload scripts, and `isTrusted` behavior
- network interception, data collection, packet capture, and scraper-oriented workflows
- existing-browser attach flows and high-risk automation scenarios
- WebDriver BiDi standard mapping and module-level semantics
- official companion Firefox fingerprint browser workflows for higher-risk environments
- comprehensive webpage-parameter analysis using waits, page source, runtime JS clues, and browser-observable network traffic

## Principles

- Prefer the official `ruyiPage` package behavior, repository documentation, and examples as the source of truth.
- Prefer real example scripts over invented patterns.
- Keep guidance task-oriented so an AI can quickly map a user request to the right examples.
- Record support caveats explicitly so advanced Firefox and BiDi behavior is not overstated.
- Keep the shared knowledge base in vendor-neutral Markdown so it can be adapted to many AI tools.

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
    ├── recipes/
    └── matrices/
```

The first version intentionally starts small. More detailed references, recipes, and support notes can be added after the core workflow is stable.

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

## Notes

- This repository is maintained independently.
- Third-party skill repositories can be useful references, but they are not treated as the authoritative source here.
- For webpage-parameter analysis tasks, the intended default is comprehensive capture after readiness, not one-shot DOM inspection.
