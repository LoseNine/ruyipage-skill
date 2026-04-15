# Touch Actions

How to simulate touch interactions for mobile-emulated pages.

## Basic Touch Gestures

```python
# Single tap
page.touch.tap(page.ele("css:#button")).perform()

# Double tap
page.touch.double_tap(page.ele("css:#button")).perform()

# Long press
page.touch.long_press(page.ele("css:#item"), duration=800).perform()
```

## Swipe

```python
# Swipe by coordinates
page.touch.swipe(x1=200, y1=500, x2=200, y2=200, duration=300).perform()

# Directional swipe helpers
page.touch.swipe_up(distance=300).perform()
page.touch.swipe_down(distance=300).perform()
page.touch.swipe_left(distance=200).perform()
page.touch.swipe_right(distance=200).perform()
```

## Pinch and Rotate

```python
# Pinch in (zoom out)
page.touch.pinch_in(cx=400, cy=400, start_gap=200, end_gap=50, duration=500).perform()

# Pinch out (zoom in)
page.touch.pinch_out(cx=400, cy=400, start_gap=50, end_gap=200, duration=500).perform()

# Rotate gesture
page.touch.rotate(cx=400, cy=400, radius=100, start_angle=0, end_angle=90).perform()
```

## Low-Level Touch Control

```python
# Manual touch sequence
page.touch.touch_down(page.ele("css:#slider")).perform()
page.touch.move_to({"x": 300, "y": 400}, duration=200).perform()
page.touch.touch_up().perform()

# Flick gesture
page.touch.flick(page.ele("css:#list"), vx=0, vy=-500, duration=100).perform()

# Release all active touches
page.touch.release_all().perform()
```

## Setup

Touch actions are most useful when combined with mobile emulation:

```python
page.emulation.set_touch_enabled(enabled=True)
page.emulation.apply_mobile_preset(user_agent="...", width=375, height=812)
```

See `docs/proxy-emulation.md` for full emulation setup.
