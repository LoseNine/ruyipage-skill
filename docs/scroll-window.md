# Scroll and Window Management

How to scroll pages/elements and control the browser window.

## Page Scrolling

```python
# Scroll to page boundaries
page.scroll.to_top()
page.scroll.to_bottom()
page.scroll.to_half()
page.scroll.to_leftmost()
page.scroll.to_rightmost()

# Scroll by pixel offset
page.scroll.down(300)
page.scroll.up(300)
page.scroll.right(300)
page.scroll.left(300)

# Scroll to a specific element
page.scroll.to_see(page.ele("css:#target"))
page.scroll.to_see(page.ele("css:#target"), center=True)

# Scroll to an absolute position
page.scroll.to_location(0, 500)
```

## Element Scrolling

Works the same way on scrollable containers:

```python
container = page.ele("css:.scroll-container")
container.scroll.to_bottom()
container.scroll.down(200)
container.scroll.to_see()   # scroll element into view
```

## Actions-Based Scrolling

For scrolling at a specific coordinate (e.g., inside a map or canvas):

```python
page.actions.scroll(0, -300, on_ele=page.ele("css:.map")).perform()
```

## Window Management

```python
# Window states
page.window.maximize()
page.window.minimize()
page.window.fullscreen()
page.window.normal()

# Resize and position
page.window.set_size(1280, 720)
page.window.set_position(100, 100)
page.window.center()                      # center on screen
page.window.center(width=1280, height=720) # center with specific size

# Get window info
info = page.window.info  # dict with x, y, width, height, state
```

## Page / Viewport Size Info

```python
page.rect.window_size       # {"width": ..., "height": ...}
page.rect.viewport_size     # inner viewport dimensions
page.rect.page_size         # full page dimensions (including scroll)
page.rect.scroll_position   # current scroll offset
page.rect.viewport_midpoint # center of the viewport
```
