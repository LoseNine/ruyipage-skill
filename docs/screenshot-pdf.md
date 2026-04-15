# Screenshot and PDF

How to capture page or element screenshots and export PDFs.

## Page Screenshot

```python
# Save to file
page.screenshot("./output/page.png")

# Full-page screenshot (scroll capture)
page.screenshot("./output/full.png", full_page=True)

# Get as bytes
img_bytes = page.screenshot(as_bytes=True)

# Get as base64
img_b64 = page.screenshot(as_base64=True)
```

## Element Screenshot

```python
ele = page.ele("css:#target")
ele.screenshot("./output/element.png")
ele_bytes = ele.screenshot(as_bytes=True)
```

## PDF Export

```python
page.pdf("./output/page.pdf")
page.save_pdf("./output/page.pdf")
```

## What Not To Do

- Don't use `full_page=True` on infinitely scrolling pages without limiting the viewport first
- Don't forget that element screenshots require the element to be in the viewport
