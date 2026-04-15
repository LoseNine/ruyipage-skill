# Console Listener and Extensions

How to monitor browser console output and manage WebExtensions.

## Console Listener

Listen for `console.log`, `console.error`, and other console messages from the page.

```python
# Start listening (all levels)
page.console.start()

# Start listening for specific levels only
page.console.start(level="error")

# Wait for a console message
entry = page.console.wait(level="error", text="failed", timeout=10)

# Get all recorded entries
entries = page.console.entries

# Filter entries
errors = page.console.get(level="error")
matches = page.console.get(text="API response")

# Register a callback for real-time monitoring
page.console.on_entry(lambda entry: print(entry))

# Clear recorded entries
page.console.clear()

# Stop listening
page.console.stop()
```

### When To Use

- Debugging JS errors during automation
- Waiting for a specific log message that signals page readiness
- Monitoring API responses logged to console

## Extension Management

Install and manage Firefox WebExtensions.

```python
# Install an extension from .xpi file or directory
page.extensions.install("./my_extension.xpi")
page.extensions.install("./extension_dir/")

# List installed extensions
installed = page.extensions.installed_extensions

# Uninstall a specific extension
page.extensions.uninstall(extension_id)

# Uninstall all extensions
page.extensions.uninstall_all()
```

### When To Use

- Adding ad blockers or privacy extensions for scraping
- Loading custom extensions for automation assistance
- Managing extension lifecycle in automated workflows
