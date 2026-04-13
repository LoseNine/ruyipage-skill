# Web Analysis Checklist

Use this checklist when the user asks to analyze webpage parameters, signatures, runtime values, or page-generated requests.

## Readiness

- did you start capture before navigation if early requests matter
- did you wait for `page.wait.doc_loaded(...)`
- did you confirm `load` or other navigation readiness when needed
- did you allow a bounded post-load capture window for late async traffic if necessary

## Page Source

- did you capture `page.html`
- did you capture `document.documentElement.outerHTML`
- did you distinguish rendered DOM from original response HTML
- did you inspect iframe content when the page structure suggests it

## JS Clues

- did you inspect inline scripts
- did you inspect external script URLs
- did you inspect runtime globals or config values on `window`
- did you re-check runtime state after the triggering user action if needed

## Network

- did you capture browser-observable requests and responses
- did you preserve `request_id`
- did you capture request body when available
- did you capture response body when available
- did you keep failed or unusual requests if they may explain gating or anti-bot behavior

## Analysis Output

- did you identify the actual target request rather than a nearby static asset
- did you explain likely parameter sources
- did you point out unresolved uncertainty rather than guessing
- did you separate evidence from inference
