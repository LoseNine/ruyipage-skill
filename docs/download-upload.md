# Download and Upload

How to handle file downloads and uploads.

## Download Management

```python
# Set download directory
page.downloads.set_path("./downloads")

# Start listening for download events
page.downloads.start()

# Trigger a download (click a link, etc.)
page.ele("css:a.download-btn").click()

# Wait for download to complete
page.downloads.wait(timeout=30)

# Wait for a specific file
page.downloads.wait(filename="report.pdf", timeout=30)

# Chain-style wait (returns download event)
event = page.downloads.wait_chain(filename="report.pdf", timeout=30)

# Verify file exists
exists = page.downloads.file_exists("./downloads/report.pdf", min_size=1)

# Wait for a file to appear on disk
page.downloads.wait_file("./downloads/report.pdf", timeout=30)

# Stop listening
page.downloads.stop()

# Clear recorded events
page.downloads.clear()
```

### Configure via Options

```python
opts = FirefoxOptions()
opts.set_download_path("./downloads")
page = FirefoxPage(opts)
```

## File Upload

For `<input type="file">` elements, use `.input()` with the file path:

```python
page.ele("css:input[type='file']").input("E:/files/photo.jpg")
```

## What Not To Do

- Don't forget to call `downloads.start()` before triggering the download
- Don't assume the file is ready immediately after the click — always use `wait` or `wait_file`
