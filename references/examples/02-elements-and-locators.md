# Elements And Locators

## Goal

Use this topic when the main task is locating page content, reading text or attributes, and choosing a selector strategy.

## Primary Examples

- `02_element_finding.py`

## Supporting Examples

- `04_wait_conditions.py`

## Main Capabilities

- `page.ele()` and `page.eles()`
- CSS, XPath, text, and attribute selectors
- reading text, attributes, links, and state
- checking whether elements are visible or enabled

## Recommended Starting Point

Start with `02_element_finding.py` for almost all DOM-reading tasks.

Add wait logic from `04_wait_conditions.py` when content loads asynchronously.

## When To Escalate

- move to `13_iframe.py` if the selector fails because the element is in a frame
- move to `14_shadow_dom.py` if the element is in shadow DOM
- move to `42_xpath_picker_complex_showcase.py` if locator discovery is difficult

## Caveats

- do not jump to XPath picker unless ordinary selectors are insufficient
- text selectors can be fragile on dynamic or localized pages

## W3C BiDi Mapping

- locator work aligns most closely with `browsingContext.locateNodes`
- user-facing selector syntax in `ruyiPage` is higher-level than raw protocol semantics
