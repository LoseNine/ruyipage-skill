# Proxy and Device Emulation

How to configure proxies and emulate device environments.

## Proxy Configuration

```python
opts = FirefoxOptions()

# HTTP/SOCKS proxy
opts.set_proxy("http://127.0.0.1:8080")
opts.set_proxy("socks5://user:pass@127.0.0.1:1080")

page = FirefoxPage(opts)
```

## Geolocation

```python
page.emulation.set_geolocation(latitude=37.7749, longitude=-122.4194, accuracy=100)
page.emulation.clear_geolocation()
```

## Timezone and Locale

```python
page.emulation.set_timezone("America/Los_Angeles")
page.emulation.set_locale("en-US")
```

## User Agent

```python
page.emulation.set_user_agent("Mozilla/5.0 ...", platform="Win32")
# Or via setter
page.set.useragent("Mozilla/5.0 ...")
```

## Viewport and Screen

```python
page.set.viewport(1280, 720, device_pixel_ratio=2)
page.emulation.set_screen_size(1920, 1080, device_pixel_ratio=2)
page.emulation.set_screen_orientation("portraitPrimary", angle=0)
```

## Mobile Preset

```python
page.emulation.apply_mobile_preset(
    user_agent="Mozilla/5.0 (iPhone; ...) ...",
    width=375,
    height=812,
)
```

## Network Simulation

```python
page.emulation.set_network_offline(enabled=True)   # simulate offline
page.emulation.set_network_offline(enabled=False)   # restore
```

## Other Emulation

```python
page.emulation.set_touch_enabled(enabled=True)
page.emulation.set_javascript_enabled(enabled=False)
page.emulation.set_bypass_csp(enabled=True)
page.emulation.set_forced_colors_mode("active")
page.emulation.set_scrollbar_type("none")
```

## Consistency with Fingerprint Browser

When using proxy + fingerprint browser, all emulation settings must align with the proxy IP's geographic context. See `docs/fingerprint-browser.md` for the consistency rules.
