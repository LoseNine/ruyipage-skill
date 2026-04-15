# Complex Page Location

How to find the correct interaction target on difficult pages.

## Typical Difficulties

- Iframe nesting (the real input lives inside nested frames)
- Dynamic entry points (textarea, contenteditable, custom input containers)
- Cloudflare-style 5-second shields and challenge transitions
- Shadow-boundary problems (closed shadow roots, layered DOM)

## Strategy

### 1. Wait for page stabilization

Don't locate immediately. Let challenges complete and dynamic content hydrate.

```python
page.get(url, wait="none")
page.handle_cloudflare_challenge(timeout=120, check_interval=2)  # if applicable
page.wait.doc_loaded(timeout=15)
```

### 2. Probe multiple candidates

Don't assume one selector is enough. Try several:

```python
candidates = [
    "css:textarea",
    'css:[contenteditable="true"]',
    "css:div.input-container",
    "css:input[type='text']",
]
target = None
for sel in candidates:
    el = page.ele(sel)
    if el:
        target = el
        break
```

### 3. Use repeated probing in bounded loops

Pages may still be loading or transitioning. Retry before giving up.

```python
import time

for attempt in range(5):
    target = page.ele("css:textarea")
    if target:
        break
    time.sleep(2)
```

### 4. Respect frame boundaries

If the target is inside an iframe, use the public frame API to navigate into it:

```python
# Discover all child frames
frames = page.get_frames()

# Get a specific frame by index, locator, or context_id
frame = page.get_frame(index=0)
# frame = page.get_frame("css:iframe#editor")

# Locate elements inside the frame
target = frame.ele("css:textarea")
```

### 5. Verify the target is interactive

The real target should receive focus, accept input, and trigger downstream behavior. If clicking a wrapper element does nothing, keep probing deeper.

## Reference

The `quickstart_cloudfare.py` example demonstrates this resilient probing style for real Cloudflare-protected pages.
