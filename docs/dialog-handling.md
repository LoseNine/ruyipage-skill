# Dialog Handling

How to handle JavaScript alert, confirm, and prompt dialogs.

## Quick Actions

```python
# Accept an alert
page.accept_alert()

# Dismiss a confirm dialog
page.dismiss_alert()

# Accept and provide text for a prompt
page.accept_prompt(text="my answer")

# Dismiss a prompt
page.dismiss_prompt()

# Generic handler
page.handle_alert(action="accept", text=None, timeout=3)
```

## Wait for a Dialog

```python
# Wait until a dialog appears
page.wait_prompt(timeout=5)

# Check if a dialog is currently open
has_dialog = page.states.has_alert
```

## Pre-configure Dialog Behavior

Set automatic handlers before triggering actions that open dialogs:

```python
# Auto-accept all alerts, auto-dismiss confirms
page.set_prompt_handler(alert="accept", confirm="dismiss")

# Auto-accept prompts with default text
page.set_prompt_handler(prompt="accept", prompt_text="default answer")

# Clear all handlers (revert to manual)
page.clear_prompt_handler()
```

Or configure at browser launch:

```python
opts = FirefoxOptions()
opts.set_user_prompt_handler("accept")  # auto-accept all dialogs
page = FirefoxPage(opts)
```

## Trigger and Handle Login Dialogs

```python
# HTTP basic auth dialog triggered by clicking a link
page.prompt_login(
    trigger_locator="css:a.login-link",
    username="user",
    password="pass",
    trigger="mouse",
    timeout=5,
)
```

## What Not To Do

- Don't try to interact with page elements while a dialog is blocking — dismiss it first
- Don't use fixed `sleep` to wait for dialogs — use `wait_prompt(timeout)` instead
