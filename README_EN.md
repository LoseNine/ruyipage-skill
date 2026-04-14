# ruyipage-skill

[中文](README.md) | English

`ruyipage-skill` is an open-source AI skill for `ruyiPage`.

This version currently focuses on one core principle:

- prefer BiDi-native behavior for automation, or use a complete JS human-like event chain with the `ruyi` property so the behavior can pass `isTrusted`-related checks
- make automation behavior humanized, randomized, and naturally paced by default
- prefer a fresh isolated `user_dir` for new identities
- when risk-control or anti-bot scenarios appear, use the official Firefox fingerprint browser when needed
- keep fingerprint changes internally consistent, especially across WebRTC, language, timezone, geolocation, speech, and IP alignment
- in real data-collection workflows, automation behavior and network capture must work together: automation triggers the real page flow, and network listeners capture the request/response chain through identifiers such as `request_id`
- on complex pages, the skill should be able to keep probing for accurate targets across iframe nesting, difficult entry points, and closed-shadow-like locator challenges, following the style of real-page handling shown in `quickstart_cloudfare.py`
- when writing code, if a `ruyiPage` API is uncertain, the skill must check the official GitHub repository and official examples first, use local source only as a secondary reference, and must not invent unsupported APIs
- the highest-priority source reference is <https://github.com/LoseNine/ruyipage>; if a local copy is behind, update it first before concluding how an API should be used
- for page-location work, the skill should first build as complete a page-source view as possible, including page source, batched source fragments, packet capture, and relevant JS clues
- locator work should advance through both a BiDi route and a full human-like JS route with `ruyi`, and should finally prefer the BiDi route when both are workable
- locator strategy should combine XPath, CSS, `browsingContext.getTree`, element sizing, and center-point XY methods instead of relying on a single selector style

## Usage

### 1. Download the repository

```bash
git clone https://github.com/LoseNine/ruyipage-skill.git
```

Or download the ZIP from GitHub.

### 2. Let the AI read the skill

Recommended reading order:

1. `SKILL.md`
2. `docs/core-principle.md`
3. `docs/humanized-automation.md`
4. `docs/fingerprint-browser.md`
5. `docs/data-capture-coordination.md`
6. `docs/complex-page-location.md`
7. `docs/page-analysis-and-location.md`

### 3. Runtime requirements

Automation is expected to use:

- the `ruyiPage` Python package
- the official `ruyiPage` repository and examples
- the official Firefox fingerprint browser when higher-risk scenarios require it

If the environment is missing, detect the gap first, then install or download what is needed. If the local reference copy is outdated, sync the official repository before continuing.

### 4. Official related projects

- `ruyiPage`: <https://github.com/LoseNine/ruyipage>
- Firefox fingerprint browser: <https://github.com/LoseNine/firefox-fingerprintBrowser>

### 5. Default browser path assumption

Default assumption:

- the Firefox browser installed under the default Windows `C` drive path is treated as the fingerprint browser in this skill

If the actual environment differs, detect the real browser path first and then decide whether explicit configuration is needed.
