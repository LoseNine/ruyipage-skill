# XPath Picker and Action Visual

Two built-in debugging tools for development and troubleshooting.

## XPath Picker

An interactive overlay that shows XPath selectors as you hover over elements. Useful for discovering the right locator on complex pages.

### Enable

```python
# Via launch
page = launch(xpath_picker=True)

# Via options
opts = FirefoxOptions()
opts.enable_xpath_picker(True)
page = FirefoxPage(opts)
```

### What It Does

- Injects an overlay panel into the page
- Highlights the element under cursor
- Shows the computed XPath in real time
- Works across iframes (auto-injects into child frames)
- Copy-ready XPath for direct use with `page.ele("xpath:...")`

### When To Use

- Discovering selectors on unfamiliar pages
- Debugging why `page.ele()` can't find a target
- Verifying that an XPath uniquely matches the intended element

## Action Visual

A debugging overlay that visualizes mouse movements, clicks, and element highlights during automation. Useful for verifying that humanized interactions are working as intended.

### Enable

```python
# Via launch
page = launch(action_visual=True)

# Via options
opts = FirefoxOptions()
opts.enable_action_visual(True)
page = FirefoxPage(opts)
```

### What It Visualizes

- Mouse movement trails (path rendering)
- Click positions and button type
- Target element highlighting with label

### When To Use

- Debugging click accuracy (is the click hitting the right element?)
- Verifying humanized mouse paths look natural
- Demonstrating automation behavior visually
- Troubleshooting why an action isn't triggering the expected behavior

## Combining Both

Both tools can be enabled simultaneously:

```python
page = launch(xpath_picker=True, action_visual=True)
```

## What Not To Do

- Don't leave these enabled in production automation — they add DOM elements and event listeners
- Don't rely on XPath Picker output without testing the XPath in `page.ele()` first
