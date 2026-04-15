# Environment Detection

How to detect and set up the ruyiPage runtime before starting automation.

## Detection Steps

### 1. Check ruyiPage installation

```bash
pip show ruyipage
```

If missing:

```bash
pip install ruyipage
```

### 2. Check Firefox browser path

```bash
# Windows default
ls "C:/Program Files/Mozilla Firefox/firefox.exe" 2>/dev/null

# Or search
where firefox 2>/dev/null
```

### 3. Check if the fingerprint browser is needed

Only needed when the task involves anti-bot pressure, multi-account isolation, or persistent identity. See `docs/fingerprint-browser.md` for details.

### 4. Decide on user_dir

- New identity → create a fresh `user_dir`
- Resuming a session → reuse the existing `user_dir`

```python
opts = FirefoxOptions()
opts.set_user_dir("./profiles/fresh_identity_001")
```

### 5. Check local source reference

If you need to verify ruyiPage APIs against source code:

```bash
cd /path/to/local/ruyipage
git fetch origin
git log HEAD..origin/main --oneline
```

If the local copy is behind, update it before relying on it:

```bash
git pull origin main
```

The official repository is always the highest-priority reference: <https://github.com/LoseNine/ruyipage>
