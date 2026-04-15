# Browser Attach

How to connect to an already-running Firefox instance instead of launching a new one.

## Direct Attach

```python
from ruyipage import attach

# Connect to a browser at a known address
page = attach(address="127.0.0.1:9222")
```

## Attach to Existing Browser

```python
from ruyipage import attach_exist_browser

# Connect and optionally select a tab
page = attach_exist_browser(address="127.0.0.1:9222")
page = attach_exist_browser(address="127.0.0.1:9222", tab_index=0)
page = attach_exist_browser(address="127.0.0.1:9222", latest_tab=True)
```

## Auto-Discover and Attach

```python
from ruyipage import auto_attach_exist_browser, find_exist_browsers

# Find all running browsers in a port range
browsers = find_exist_browsers(
    host="127.0.0.1",
    start_port=9200,
    end_port=9300,
    timeout=3,
    max_workers=20,
)

# Auto-discover and attach to the first available browser
page = auto_attach_exist_browser(
    host="127.0.0.1",
    start_port=9200,
    end_port=9300,
)
```

## Process-Based Discovery

```python
from ruyipage import find_exist_browsers_by_process, auto_attach_exist_browser_by_process

# Find browsers by process detection (no port scanning)
browsers = find_exist_browsers_by_process()

# Auto-attach via process detection
page = auto_attach_exist_browser_by_process()
```

## Via Options

```python
from ruyipage import FirefoxOptions, FirefoxPage

opts = FirefoxOptions()
opts.set_address("127.0.0.1:9222")
opts.existing_only(True)   # don't launch new browser, only connect
page = FirefoxPage(opts)
```

## When To Use

- Connecting to a browser started manually or by another process
- Reusing a long-running browser session across script restarts
- Debugging — attach to a browser you're interacting with manually
