# Cookie and Storage Management

How to manage cookies, localStorage, and sessionStorage.

## Cookies

```python
# Get all cookies (simple format: list of name=value)
cookies = page.get_cookies()

# Get all cookies with full info (domain, path, expiry, etc.)
cookies = page.get_cookies(all_info=True)

# Filter by name or domain
cookies = page.get_cookies_filtered(name="session_id")
cookies = page.get_cookies_filtered(domain=".example.com", all_info=True)

# Set cookies
page.set_cookies([
    {"name": "token", "value": "abc123", "domain": ".example.com"},
    {"name": "lang", "value": "en"},
])

# Delete cookies
page.delete_cookies(name="token")
page.delete_cookies(domain=".example.com")
```

## localStorage

```python
storage = page.local_storage

# Set / get / remove
storage.set("key", "value")
val = storage.get("key")
storage.remove("key")

# Clear all
storage.clear()

# List all keys and items
keys = storage.keys()
items = storage.items()

# Dict-like access
storage["key"] = "value"
val = storage["key"]
del storage["key"]
"key" in storage   # True/False
len(storage)       # item count
```

## sessionStorage

```python
# Same API as localStorage
session = page.session_storage
session.set("temp", "data")
val = session.get("temp")
```

## What Not To Do

- Don't set cookies without specifying `domain` when working with cross-domain scenarios
- Don't confuse cookies (sent with HTTP requests) with localStorage (client-side only)
