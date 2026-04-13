# Object Model

This file summarizes the main user-facing object areas in `ruyiPage`.

## Startup Layer

### `FirefoxPage`

Use when the script wants a direct page object and explicit browser session control.

### `launch()`

Use when the script wants a shorter startup path with common parameters.

### `FirefoxOptions`

Use when browser path, user directory, private mode, picker settings, or launch-time configuration matter.

## Page And Element Layer

### page object

Handles navigation, waits, selectors, JavaScript execution, screenshots, tabs, and high-level workflow control.

### element object

Handles text, attributes, state, clicks, input, and element-level JavaScript.

## Interaction Layer

### `page.actions`

Handles action chains, keyboard sequences, pointer movement, drag, touch-like behavior, and more realistic interaction flows.

## Capability Subsystems

### `page.network`

Used for network-oriented controls such as collectors, headers, and cache-related behavior.

### `page.navigation`

Used for navigation event coordination and higher-precision navigation reasoning.

### `page.downloads`

Used for download behavior and download event flow.

### `page.console`

Used for console log observation.

### `page.emulation`

Used for user agent, locale, timezone, screen, touch, and related override capabilities.

### `page.contexts`

Used for browsing-context level management.

### `page.browser_tools`

Used for browser and user-context oriented operations beyond a single page view.

## Boundary Guidance

- Prefer page and element APIs first.
- Use `page.actions` when interaction choreography or fidelity matters.
- Use `page.network` and event-oriented APIs when the task is really about traffic, not just DOM.
- Use `standards/` when explaining how these layers map to WebDriver BiDi modules.
