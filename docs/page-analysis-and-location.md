# Page Analysis And Location

## Goal

Before serious page automation locating work, build a usable full-page view and then narrow down the true target step by step.

## Rule 1: Build a complete enough page-source view first

Do not rush straight into selectors.

The skill should gather and combine:

- rendered page source
- page-source fragments in batches when the full page is too large to inspect at once
- network packets and request/response evidence
- relevant JS clues

If the source is too large, collect it in batches until the working view is complete enough for locator analysis.

## Rule 2: Advance BiDi and JS locating together

When the page is difficult:

- advance a BiDi-grounded route
- advance a full human-like JS route with `ruyi`
- compare which route can really reach the intended element or data

If both are workable, prefer the BiDi route.

## Rule 3: Use multiple locating methods

Do not rely on one selector style.

Useful locating methods include:

- XPath
- CSS
- `browsingContext.getTree`
- frame-path inspection
- element geometry
- center-point XY probing

## Recommended Sequence

1. collect page source view
2. collect packet and JS clues if the page is dynamic
3. inspect frame and tree structure
4. try CSS and XPath candidates
5. verify geometry and center-point behavior when needed
6. advance BiDi and full-`ruyi` JS routes step by step
7. keep the route that actually reaches the target reliably
8. if both work, keep the BiDi route

## What Counts As Complete Enough Source View

A useful view usually includes:

- current rendered source
- key dynamic regions
- relevant frame structure
- packet evidence for data-driven pages
- JS clues that explain dynamic rendering or event behavior

## What Not To Do

- do not rely on one CSS or XPath guess before understanding the page shape
- do not stop after the first failed route if another supported route is still available
- do not choose the JS route by default when the BiDi route works equally well
- do not ignore packet evidence on pages whose useful data is rendered dynamically from API responses
