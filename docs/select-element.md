# Select Element

How to interact with `<select>` dropdown elements.

## Basic Usage

```python
sel = page.ele("css:select#country")

# Select by visible text
sel.select.by_text("China")

# Select by value attribute
sel.select.by_value("cn")

# Select by index (0-based)
sel.select.by_index(0)

# Shortcut: select by text or index
sel.select("China")
sel.select(0)
```

## Multi-Select

```python
sel = page.ele("css:select[multiple]")

# Check if multi-select
is_multi = sel.select.is_multi

# Select multiple options
sel.select.by_text("Option A")
sel.select.by_text("Option B")

# Select all
sel.select.select_all()

# Deselect
sel.select.cancel_by_text("Option A")
sel.select.cancel_by_index(0)
sel.select.deselect_all()
```

## Read State

```python
# Get all options
options = sel.select.options

# Get current selection
selected = sel.select.selected_option
```
