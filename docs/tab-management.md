# Tab Management

How to manage multiple tabs in ruyiPage.

## Open and Switch

```python
# Open a new tab
tab = page.new_tab("https://example.com")

# Open in background (don't switch to it)
bg_tab = page.new_tab("https://example.com", background=True)

# Get a tab by index (1-based), title, or URL substring
tab = page.get_tab(1)
tab = page.get_tab(title="Dashboard")
tab = page.get_tab(url="example.com")

# Get all tabs matching a filter
tabs = page.get_tabs(url="example.com")

# Get the most recently opened tab
tab = page.latest_tab
```

## Tab Info

```python
# Number of open tabs
count = page.tabs_count

# List of all tab IDs
ids = page.tab_ids
```

## Close Tabs

```python
# Close the current tab
page.close()

# Close all tabs except specified ones
page.close_other_tabs()               # keep current tab only
page.close_other_tabs(tab)            # keep a specific tab
page.close_other_tabs([tab1, tab2])   # keep multiple tabs

# Quit the browser entirely
page.quit(timeout=5, force=False)
```

## Save Page

```python
# Save current page as HTML or PDF
path = page.save("./output", name="page", as_pdf=True)
```

## What Not To Do

- Don't assume `page` always points to the same tab — opening a new tab may change the active context
- Don't forget to use `background=True` when opening utility tabs that shouldn't steal focus
