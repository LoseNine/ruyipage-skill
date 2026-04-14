# Data Capture Coordination

## Rule

In real webpage data-collection workflows, automation behavior and network capture must work together.

Automation is not separate from packet capture.

- automation behavior triggers the real page state changes
- network listening, interception, and collectors capture the request and response chain
- the result should be explained through linked evidence rather than one isolated observation

## What To Learn From Example 43

The key pattern is not only "perform an action" and not only "listen to packets".

The key pattern is:

1. open the real page
2. wait for readiness
3. start the relevant collector or listener before the trigger action
4. use human-like page actions to trigger the target request
5. wait for the matching packet
6. use `request_id` or equivalent request-chain evidence to fetch the response body
7. continue or retry based on the actual response content

## Coordination Requirements

### 1. Trigger and capture are one workflow

Do not design them separately.

- the action should be chosen to reproduce the page's real behavior
- the listener should be started early enough to capture the request
- the captured data should be tied back to the action that triggered it

### 2. Start listeners first

For request and response capture, start the relevant listener, `listen`, collector, or interception path before the action that triggers the network flow.

### 3. Use realistic trigger behavior

For sensitive pages, the trigger action should use:

- BiDi-grounded behavior first
- or a full `ruyi` JS event chain if JS-side control is required
- humanized timing and pacing

### 4. Correlate request and response

Prefer a request chain that can be traced through identifiers such as:

- `request_id`
- request URL and method
- request body
- response status
- response body

### 5. Keep the loop evidence-driven

If the response shows anti-bot or environment abnormality, do not stop at the first packet. Re-check the environment assumptions and repeat the trigger-capture loop when appropriate.

## Preferred Capture Pattern

1. page ready
2. collector/listener ready
3. trigger action ready
4. perform humanized trigger
5. wait for packet
6. correlate request and response
7. inspect body
8. decide whether to continue, retry, or escalate

## What Not To Do

- do not trigger the action first and only then start listening
- do not rely on DOM alone when the useful data is in packets
- do not treat one matching URL as enough without checking the linked request and response data
- do not ignore abnormal-response bodies when deciding whether the collection succeeded
