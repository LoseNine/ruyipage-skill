# Page Analysis And Location

How to build a complete page-source view before committing to locator decisions.

## Why This Matters

On complex or dynamic pages, the first visible DOM node is often not the real interactive target. Jumping straight into selectors without understanding the page structure leads to fragile, broken automation.

## Step-by-Step Approach

### 1. Collect page source view

```python
# Get rendered page source
source = page.run_js("return document.documentElement.outerHTML")

# If too large, collect in batches
head = page.run_js("return document.head.outerHTML")
body_top = page.run_js("return document.body.innerHTML.substring(0, 50000)")
```

### 2. Inspect frame structure

```python
# Discover all child frames
frames = page.get_frames()

# Get a specific frame by index or locator
frame = page.get_frame(index=0)
# frame = page.get_frame("css:iframe#content")

# Locate elements inside the frame
target = frame.ele("css:textarea")
```

### 3. Collect network evidence for dynamic pages

Pages that render data from API responses need packet inspection too. See `docs/data-capture-coordination.md` for the capture pattern.

### 4. Try CSS and XPath candidates

```python
# CSS
target = page.ele("css:textarea")

# XPath (with xpath_picker enabled)
target = page.ele("xpath://div[@class='editor']//textarea")
```

### 5. Verify with geometry when needed

When selectors are ambiguous, check element position and size:

```python
# Use center-point XY to confirm you're hitting the right element
page.actions.move_to({"x": 500, "y": 300}).click().perform()
```

### 6. Advance BiDi and JS routes in parallel

Try both approaches until one proves workable. If both can reach the target, keep the BiDi route (it's more reliable and natively trusted).

## What Not To Do

- Don't guess a CSS selector before understanding the page shape
- Don't stop after the first failed route if other methods are available
- Don't default to the JS route when the BiDi route works equally well
- Don't ignore network evidence on pages whose content comes from API responses
