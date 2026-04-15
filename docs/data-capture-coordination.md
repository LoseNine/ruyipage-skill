# Data Capture Coordination

How to combine page automation with network capture for scraping workflows.

## Core Pattern

Automation triggers real page behavior. Network capture grabs the request/response chain. They are one workflow, not two separate tasks.

**The sequence always is:**

1. Page is ready
2. Start the listener/collector **before** the trigger action
3. Perform the humanized trigger action
4. Wait for the matching packet
5. Correlate request and response through `request_id` or URL
6. Inspect the response body
7. Decide: continue, retry, or escalate

## Example: New Intercept API (recommended)

Based on the pattern from `40_scraper_packet_capture.py`:

```python
from ruyipage import FirefoxOptions, FirefoxPage

page = FirefoxPage(FirefoxOptions())
page.get("https://example.com/search")
page.wait.doc_loaded()

# Step 1: start intercept BEFORE the trigger action
page.intercept.start(handler=None, phases=["beforeRequestSent"], collect_response=True)

# Step 2: trigger the search (humanized)
page.ele("css:input").input("query", clear=True)
page.actions.press(Keys.ENTER).perform()

# Step 3: wait and read response
req = page.intercept.wait(timeout=15)
print(req.response_body)
req.continue_request()
page.intercept.stop()
```

## Example: Legacy Listen + Collector API

Based on the pattern from `43_zhipin_xpath_picker.py`:

```python
# Step 1: register collector and listener BEFORE the action
collector = page.network.add_data_collector(
    ["responseCompleted"], data_types=["response"]
)
page.listen.start("api.example.com/data", method="POST")

# Step 2: trigger action
page.actions.move_to({"x": 500, "y": 300}).click().perform()

# Step 3: wait, correlate, read
packet = page.listen.wait(timeout=30)
body = collector.get(packet.request_id, data_type="response")
page.listen.stop()
collector.stop()
```

## What Not To Do

- Don't trigger the action first and then start listening — you'll miss the packet
- Don't rely on DOM scraping alone when the useful data is in API responses
- Don't treat one matching URL as success without checking the response body
- Don't ignore abnormal responses (anti-bot blocks, empty bodies) — re-check environment and retry
