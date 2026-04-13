# iframe Shadow XPath

## Goal

Use this topic when ordinary selectors are blocked by DOM boundaries such as frames, nested frames, shadow roots, or real-site complexity that benefits from picker assistance.

## Primary Examples

- `13_iframe.py`
- `14_shadow_dom.py`
- `42_xpath_picker_complex_showcase.py`

## Supporting Examples

- `43_zhipin_xpath_picker.py`
- `44_shopee_userdir_xpath.py`

## Main Capabilities

- traverse iframe boundaries
- work with nested frame structures
- access shadow DOM
- use XPath picker to accelerate locator discovery
- turn picker output into real script hypotheses

## Recommended Starting Point

Start with `13_iframe.py` when content is inside frames.

Use `14_shadow_dom.py` when a shadow boundary is the real reason the selector fails.

Use `42_xpath_picker_complex_showcase.py` when the user wants interactive locator discovery.

## When To Escalate

- move to `43_zhipin_xpath_picker.py` or `44_shopee_userdir_xpath.py` only when real-site workflow details matter
- combine with `41_private_mode_userdir.py` or attach flows when the target site depends on persistent browser state

## Caveats

- picker output is a starting point, not a permanent guarantee of stability
- real-site XPath workflows should be explained as operationally sensitive

## W3C BiDi Mapping

- frame and DOM-boundary work aligns mostly with `browsingContext`
- picker-assisted discovery is higher-level workflow support, not a raw W3C concept
