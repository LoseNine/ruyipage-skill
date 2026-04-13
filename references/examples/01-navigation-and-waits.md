# Navigation And Waits

## Goal

Use this topic when the task is mainly about page transitions, loading states, waits, scrolling, and stable step ordering.

## Primary Examples

- `01_basic_navigation.py`
- `04_wait_conditions.py`
- `10_scrolling.py`

## Supporting Examples

- `19_pdf_printing.py`

## Main Capabilities

- navigate forward, back, refresh, and re-open
- wait for stable page markers
- wait for elements to appear, disappear, or change state
- scroll to the right content before interacting
- structure actions around page readiness rather than timing guesses

## Recommended Starting Point

Start with `01_basic_navigation.py` for normal page movement.

Use `04_wait_conditions.py` when the real problem is sequencing and reliability.

Use `10_scrolling.py` when interaction depends on viewport visibility.

## When To Escalate

- move to `24_navigation_events.py` when event-level reasoning is needed
- move to `13_iframe.py` if the content is not in the main document
- move to `31_network_events.py` if navigation timing is tied to network behavior

## Caveats

- explicit waits are generally safer than blind sleeps
- scrolling can be necessary even when selectors are correct

## W3C BiDi Mapping

- `browsingContext.navigate`
- `browsingContext.reload`
- `browsingContext.traverseHistory`
- navigation-related `browsingContext.*` events
