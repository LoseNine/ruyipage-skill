# WebDriver BiDi Overview

WebDriver BiDi is the bidirectional browser automation protocol that underlies much of `ruyiPage`'s Firefox-oriented capability model.

## Core Ideas

- commands are asynchronous requests sent by the local controller
- responses may complete out of order
- events stream from the browser to the controller
- modules group related commands and events
- subscriptions control which events the client receives

## Important Protocol Areas

- session lifecycle
- browser and user context management
- browsing context navigation and events
- network interception and data collection
- script execution, realms, and preload scripts
- input actions
- storage and cookies
- logging and web extensions

## Why This Matters For `ruyiPage`

`ruyiPage` is not just a random wrapper around browser automation. Many of its distinctive features align closely with WebDriver BiDi concepts, especially in Firefox-oriented flows.

That means an AI should:

- explain high-level `ruyiPage` code in user-facing terms first
- mention the corresponding BiDi module when that improves accuracy
- avoid confusing protocol primitives with convenience methods
