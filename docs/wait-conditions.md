# Wait Conditions

How to wait for various page and element states.

## Page Waits (`page.wait`)

```python
# Simple delay (seconds)
page.wait(2)

# Wait for page load states
page.wait.doc_loaded(timeout=15)         # DOM fully loaded
page.wait.load_start(timeout=10)         # navigation started

# Wait for an element to appear
page.wait.ele("css:#result", timeout=10)

# Wait for element visibility changes
page.wait.ele_displayed("css:#modal", timeout=10)
page.wait.ele_hidden("css:#loading", timeout=10)
page.wait.ele_deleted("css:#splash", timeout=10)

# Wait for title / URL changes
page.wait.title_is("Dashboard", timeout=10)
page.wait.title_contains("Dashboard", timeout=10)
page.wait.url_contains("/dashboard", timeout=10)
page.wait.url_change(page.url, timeout=10)

# Wait for a JS condition to become truthy
page.wait.js_result("return document.readyState === 'complete'", timeout=10)
```

## Element Waits (`ele.wait`)

```python
ele = page.ele("css:#target")

# Simple delay
ele.wait(1)

# Visibility / interactability
ele.wait.displayed(timeout=10)
ele.wait.hidden(timeout=10)
ele.wait.enabled(timeout=10)
ele.wait.disabled(timeout=10)
```

## Page States (`page.states`)

Quick boolean checks without waiting:

```python
page.states.is_loaded     # True if page load is complete
page.states.is_alive      # True if browser connection is alive
page.states.is_loading    # True if page is currently loading
page.states.ready_state   # "loading" / "interactive" / "complete"
page.states.has_alert     # True if a dialog is open
```

## Element States (`ele.states`)

```python
ele.states.is_displayed    # visible on page
ele.states.is_enabled      # not disabled
ele.states.is_checked      # checkbox/radio checked
ele.states.is_selected     # option selected
ele.states.is_in_viewport  # visible in current viewport
ele.states.has_rect        # has bounding box
```

## What Not To Do

- Don't use `time.sleep()` when a specific `page.wait.*` condition exists
- Don't poll in a loop when `page.wait.js_result()` can express the condition directly
