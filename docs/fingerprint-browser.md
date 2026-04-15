# Fingerprint Browser

When and how to use the official Firefox fingerprint browser for anti-bot scenarios.

## Official Project

<https://github.com/LoseNine/firefox-fingerprintBrowser>

## When To Use

- The site has risk-control or anti-bot detection
- Persistent identity matters across sessions
- Multiple accounts require stronger fingerprint separation

If the task doesn't involve anti-bot pressure, a regular Firefox instance is fine.

## Default Path

This skill assumes the Firefox browser at the default Windows `C` drive install path is the fingerprint browser. If the actual path differs, detect it first:

```bash
# Detect Firefox path on Windows
where firefox 2>/dev/null || ls "C:/Program Files/Mozilla Firefox/firefox.exe" 2>/dev/null
```

Then set it explicitly:

```python
opts = FirefoxOptions()
opts.set_browser_path(r"C:\Program Files\Mozilla Firefox\firefox.exe")
```

## Consistency Rules

All fingerprint traits in one profile must align with the effective IP context:

| Trait | Must match |
|---|---|
| WebRTC local IP | The proxy/VPN IP |
| Language / locale | The IP's geographic region |
| Timezone | The IP's timezone |
| Geolocation | The IP's coordinates |
| Speech voices | The language setting |

Never mix traits from unrelated identities in one profile.
