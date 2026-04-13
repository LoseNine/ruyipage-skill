# XPath Picker Workflow

## Use This Recipe When

- the page is hard to inspect manually
- iframe or shadow DOM structure makes locator work slow
- the user wants a fast path from page exploration to locator hypothesis

## Recommended Example Path

1. `42_xpath_picker_complex_showcase.py`
2. `13_iframe.py`
3. `14_shadow_dom.py`
4. `43_zhipin_xpath_picker.py` or `44_shopee_userdir_xpath.py` when real-site details matter

## Default Strategy

1. Determine whether the DOM difficulty is due to frames, shadow DOM, or real-site complexity.
2. Use the picker to discover likely locator paths.
3. Simplify or validate the picked locator rather than assuming it is final.
4. Convert the working locator into a maintainable page script.

## What The AI Should Produce

- the likely best locator candidate
- any needed frame or shadow traversal steps
- a simpler fallback selector if one exists
- a warning if the page is too dynamic for long-term XPath stability

## Common Failure Modes

- copying the picker output without simplification
- ignoring frame boundaries
- assuming a working real-site XPath will stay stable forever

## Related References

- `references/examples/06-iframe-shadow-xpath.md`
- `references/support-caveats.md`
