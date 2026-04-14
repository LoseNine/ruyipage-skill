# Complex Page Location

## Goal

This skill should remain able to find the correct interaction point on difficult pages.

## Typical Difficult Cases

- iframe nesting
- multiple DOM layers before the real input target appears
- dynamic input entry points
- pages protected by 5-second shield or Cloudflare-style transitions
- shadow-boundary problems, including cases that behave like closed shadow-root locating challenges

## Reference Style

Use the locating style shown by `quickstart_cloudfare.py` as the model for difficult real pages.

Key ideas from that style:

1. do not assume one selector is enough
2. probe multiple candidate entry points
3. retry over time while the page is still stabilizing
4. prefer the actual interactive target over the first visible container

## Preferred Locating Strategy

### 1. Wait for page stabilization first

- let the page reach a usable state
- allow for challenge pages, delayed hydration, or shield transitions

### 2. Probe multiple candidate targets

Examples of candidates:

- `textarea`
- `[contenteditable="true"]`
- custom input containers
- page-specific visible action zones

### 3. Use repeated probing rather than one-shot locating

- retry in bounded loops
- re-check after page transitions
- re-check after challenge-handling logic completes

### 4. Respect DOM boundaries

- if the page uses iframe nesting, locate through the correct frame path
- if the page behaves like a shadow-boundary problem, treat it as a layered locating problem rather than assuming the main DOM is enough

### 5. Verify the target is truly interactive

The real target should be able to:

- receive focus
- accept input or click behavior
- trigger the intended downstream page reaction

## Practical Rule

On difficult pages, correct locating is often an iterative discovery process, not a single selector lookup.

## What Not To Do

- do not stop after the first failed selector
- do not assume the visible wrapper is the true input target
- do not ignore page-transition time when shields or challenge pages are involved
- do not treat closed-shadow-like behavior as proof that the task is impossible; instead continue layered probing until the real interaction point is identified or the current layer is exhausted
