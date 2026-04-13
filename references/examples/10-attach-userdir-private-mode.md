# Attach Userdir Private Mode

## Goal

Use this topic when the task depends on reusing a browser session, attaching to a prepared browser, persistent profiles, private mode, proxies, or operational browser setup.

## Primary Examples

- `38_proxy_auth_ipinfo.py`
- `39_attach_exist_browser.py`
- `41_private_mode_userdir.py`

## Main Capabilities

- attach to an already running browser
- reuse existing session state
- compare temporary sessions, private mode, and persistent `user_dir`
- reason about operational setup rather than only script code

## Recommended Starting Point

Start with `39_attach_exist_browser.py` when the browser already exists.

Use `41_private_mode_userdir.py` when the user asks about profile reuse or private mode behavior.

Use `38_proxy_auth_ipinfo.py` when proxy-auth setup is directly relevant.

## When To Escalate

- consult `references/fingerprint-browser-guide.md` when stronger fingerprint stability or per-profile identity is the real need
- combine with user-context examples when multiple identities must coexist safely

## Caveats

- attach and profile workflows are operationally sensitive
- browser state, port discovery, and profile setup can dominate reliability

## W3C BiDi Mapping

- attach flows are partly operational rather than pure W3C concepts
- context and profile-related behavior aligns mainly with `browser` and `browsingContext`
