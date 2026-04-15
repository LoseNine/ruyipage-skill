# Core Principle

The priority system behind every automation decision in this skill.

## Priority Order

### 1. BiDi-native behavior first

BiDi actions go through the browser's own trusted input pipeline. They don't need `isTrusted` workarounds and are the most reliable path for sensitive automation.

### 2. Full JS event chain as fallback

When BiDi can't reach the target (e.g., custom input containers, shadow DOM internals), use JS — but model the complete human-like event sequence.

**Why this matters:** A bare `dispatchEvent` produces `isTrusted: false`. Many sites check this property. BiDi-native actions (like `page.ele().input()` and `page.actions`) go through the browser's trusted input pipeline, producing `isTrusted: true` events automatically. Only fall back to `run_js` for DOM queries or non-input operations.

**Example — BiDi vs JS input:**

```python
# Preferred: BiDi path — natively trusted
page.ele("css:textarea").input("hello", clear=True)

# Also trusted: actions chain
page.actions.move_to(page.ele("css:textarea")).click().perform()
page.actions.type("hello", interval=80).perform()

# JS fallback — for DOM queries / non-input operations only
# Note: JS dispatchEvent produces isTrusted: false, avoid for sensitive inputs
source = page.run_js("return document.querySelector('textarea').value")
```

### 3. Multi-layered locating

For difficult pages, combine multiple methods rather than betting on one selector:

- CSS / XPath selectors
- `page.get_frames()` / `page.get_frame()` for frame inspection
- Element geometry and center-point XY probing
- BiDi route and JS route advanced in parallel

When both routes reach the target, keep the BiDi route.

### 4. API grounding

When uncertain about a ruyiPage API:

1. Check the official GitHub repository: <https://github.com/LoseNine/ruyipage>
2. Check the examples directory (files named `00_quickstart.py` through `45_*.py`)
3. Use local source copies only as secondary reference — update them first if behind
4. Never write invented or unsupported APIs
