# Core Basics

## Goal

Use this topic for the smallest working `ruyiPage` scripts and for first-step environment validation.

## Primary Examples

- `00_quickstart.py`
- `06_screenshot.py`

## Supporting Examples

- `15_comprehensive.py`

## Main Capabilities

- create a page session
- open a URL
- read title and URL
- capture screenshots
- validate that the local environment is working

## Recommended Starting Point

Start with `00_quickstart.py` if the user needs the smallest runnable script.

Use `06_screenshot.py` when proof-of-state or visual debugging is part of the task.

## When To Escalate

- move to `01_basic_navigation.py` when navigation sequencing matters
- move to `04_wait_conditions.py` when state transitions matter
- move to `02_element_finding.py` when selectors are needed

## Caveats

- a successful quickstart only validates the local baseline, not a real-site workflow
- for higher-risk sites, basic startup success does not prove anti-detection stability

## W3C BiDi Mapping

- broad alignment with `session` and `browsingContext`
- screenshots align conceptually with `browsingContext.captureScreenshot`
