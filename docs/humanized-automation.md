# Humanized Automation

How to make ruyiPage automation look human rather than mechanical.

## Timing

- Use bounded random delays instead of fixed `sleep(2)` everywhere
- Vary the interval between keystrokes (e.g., `interval=80` gives natural typing rhythm)
- Add natural pauses between action groups, not between every single action

**Example:**

```python
import random, time

# Bad: rigid fixed delay
time.sleep(2)
page.ele("css:input").input("query")
time.sleep(2)
page.actions.press(Keys.ENTER).perform()

# Good: bounded randomness
time.sleep(random.uniform(0.8, 2.5))
page.ele("css:input").input("query", clear=True)
time.sleep(random.uniform(0.3, 1.0))
page.actions.press(Keys.ENTER).perform()
```

## Interaction Order

Preserve realistic event ordering. A human doesn't just type — they focus the element, pause, type with varying speed, then press Enter.

```python
# Natural sequence
page.ele("css:input").click()                              # focus
time.sleep(random.uniform(0.2, 0.6))                       # brief pause
page.actions.type("search term", interval=80).perform()    # type naturally
time.sleep(random.uniform(0.3, 0.8))                       # think pause
page.actions.press(Keys.ENTER).perform()                   # submit
```

## What Not To Do

- Don't use identical delays in a loop — the repetition pattern is detectable
- Don't skip the focus step before typing
- Don't fire actions at machine speed with zero delays
