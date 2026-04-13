# Emulation And Browser Control

## Goal

Use this topic when the task depends on environment overrides, mobile-like behavior, browser control features, or extension-related setup.

## Primary Examples

- `21_emulation.py`
- `22_web_extension.py`
- `27_emulation_advanced.py`

## Supporting Examples

- `21_mobile_google_emulation.py`

## Main Capabilities

- user agent overrides
- locale, timezone, geolocation, and screen-related settings
- touch-related environment settings
- browser-side control features such as extension handling
- mobile-style scenario experimentation

## Recommended Starting Point

Start with `21_emulation.py` for the broad feature survey.

Use `27_emulation_advanced.py` when validation depth matters.

Use `22_web_extension.py` only when extension operations are genuinely needed.

## When To Escalate

- move to `references/fingerprint-browser-guide.md` when the task is really about stronger fingerprint control rather than simple emulation
- move to real-site mobile examples only when the site-specific workflow matters

## Caveats

- not all emulation surfaces should be described as equally stable in every Firefox environment
- emulation is not the same thing as a full fingerprint-controlled browser identity

## W3C BiDi Mapping

- strong alignment with the `emulation` module
- extension work aligns with `webExtension`
