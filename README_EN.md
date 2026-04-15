# ruyipage-skill

[中文](README.md) | English

`ruyipage-skill` is an open-source AI skill for `ruyiPage` that guides AI to follow correct practices when writing ruyiPage automation scripts.

Core principles:

1. **BiDi first** — prefer BiDi-native behavior; when JS interaction is needed, use a complete human-like event chain with `ruyi` to pass `isTrusted` checks
2. **Humanization** — random delays, natural pacing, realistic interaction ordering
3. **Identity isolation** — fresh `user_dir` for each new identity
4. **Fingerprint consistency** — WebRTC, language, timezone, geolocation must align with the effective IP
5. **API grounding** — uncertain APIs must be verified against the official repository; never invent unsupported APIs

## Usage

### 1. Download the repository

```bash
git clone https://github.com/LoseNine/ruyipage-skill.git
```

Or download the ZIP from GitHub.

### 2. Let the AI read the skill

The AI only needs to read `SKILL.md` first — it contains the core rules and a quick API reference.

`SKILL.md` then guides the AI to read the relevant doc based on the current task:

| Scenario | Document |
|---|---|
| Priority system | `docs/core-principle.md` |
| Humanized interaction | `docs/humanized-automation.md` |
| Fingerprint browser | `docs/fingerprint-browser.md` |
| Environment setup | `docs/environment-detection.md` |
| Network capture coordination | `docs/data-capture-coordination.md` |
| Complex page locating | `docs/complex-page-location.md` |
| Page analysis and locating | `docs/page-analysis-and-location.md` |

### 3. Runtime requirements

- `ruyiPage` Python package (`pip install ruyipage`)
- Official `ruyiPage` repository and examples
- Official Firefox fingerprint browser when higher-risk scenarios require it

### 4. Official related projects

- `ruyiPage`: <https://github.com/LoseNine/ruyipage>
- Firefox fingerprint browser: <https://github.com/LoseNine/firefox-fingerprintBrowser>
