---
name: ruyipage-skill
description: AI skill for ruyiPage browser automation. Use this skill whenever the user wants to automate Firefox with ruyiPage, write ruyiPage scripts, handle anti-bot challenges, capture network data, locate elements on complex pages, or work with the ruyiPage fingerprint browser. Do not trigger for generic Selenium/Playwright/Puppeteer tasks that have nothing to do with ruyiPage.
version: "1.1"
last_updated: 2026-04-14
---

# RuyiPage Skill

## Core Principles

1. **BiDi first.** When ruyiPage exposes a BiDi-grounded interaction, use that path. BiDi actions are natively trusted by the browser and don't need workarounds.

2. **BiDi for input, JS for queries.** BiDi-native actions (`page.ele().input()`, `page.actions`) produce `isTrusted: true` events automatically. Use `run_js` only for DOM queries or non-input operations — never for sensitive input, as `dispatchEvent` produces `isTrusted: false`.

3. **Humanize everything.** Use bounded randomness for delays, natural pacing between actions, and realistic interaction ordering. Rigid fixed-timing loops get detected.

4. **Isolate identities.** Prefer a fresh `user_dir` for each new identity. Only reuse an existing profile when the task explicitly needs persisted session state.

5. **API grounding.** If a ruyiPage API is uncertain, check the official repository (<https://github.com/LoseNine/ruyipage>) and its examples first. Never invent unsupported APIs.

## Quick API Reference

```python
# Simple launch
from ruyipage import launch
page = launch(headless=False)

# Explicit configuration
from ruyipage import FirefoxOptions, FirefoxPage
opts = FirefoxOptions()
opts.set_user_dir("./my_profile")      # identity isolation
page = FirefoxPage(opts)

# Element interaction
page.ele("css:textarea").click()
page.ele("css:textarea").input("hello", clear=True)

# Actions chain (humanized)
from ruyipage import Keys
page.actions.move_to({"x": 500, "y": 300}).click().perform()
page.actions.type("search term", interval=80).press(Keys.ENTER).perform()

# Network capture (new intercept API)
page.intercept.start(handler=None, phases=["beforeRequestSent"], collect_response=True)
req = page.intercept.wait(timeout=10)
body = req.response_body
req.continue_request()

# Cloudflare challenge
page.handle_cloudflare_challenge(timeout=120, check_interval=2)
```

## When To Read Which Doc

Read only what your current task needs:

| Task scenario | Read this |
|---|---|
| Understanding the full priority system | `docs/core-principle.md` |
| Writing humanized interaction code | `docs/humanized-automation.md` |
| Anti-bot / fingerprint / multi-account | `docs/fingerprint-browser.md` |
| Setting up the runtime environment | `docs/environment-detection.md` |
| Scraping with network capture | `docs/data-capture-coordination.md` |
| Locating elements on difficult pages | `docs/complex-page-location.md` |
| Building full page-source view before locating | `docs/page-analysis-and-location.md` |
