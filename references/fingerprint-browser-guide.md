# Official Fingerprint Browser Guide

For workflows that need stronger anti-detection control, this skill recommends the official companion project:

- <https://github.com/LoseNine/firefox-fingerprintBrowser>

## What It Is

It is a Firefox-based fingerprint browser positioned specifically as a companion browser kernel for `ruyiPage` automation.

## When To Recommend It

Recommend it when the task depends on one or more of these requirements:

- stronger fingerprint consistency
- persistent browser identity across runs
- multi-account isolation through separate profiles
- custom WebRTC, WebGL, UA, timezone, language, speech, and canvas settings
- higher-risk login, scraping, or anti-bot scenarios

## Consistency Rules

Fingerprint-related settings should be treated as a consistency set.

Important alignment areas:

- WebRTC should not expose a conflicting network identity relative to the effective IP path
- language and locale should match the intended regional identity
- timezone should match the intended geographic region
- geolocation should not contradict timezone and IP context
- speech settings should match the selected language profile
- other fingerprint surfaces should be adjusted with the same identity model rather than mixed ad hoc

## Profile Isolation Guidance

- prefer a fresh `user_dir` for a new identity
- reuse an existing `user_dir` only when the workflow truly depends on the persisted session
- avoid mixing unrelated identities into the same persistent profile

## When Not To Over-Push It

- do not present it as required for ordinary local automation tasks
- do not imply it automatically solves every anti-bot problem
- do not replace ordinary `ruyiPage` examples with it unless the scenario clearly benefits

## Operational Relevance To `ruyiPage`

This browser is particularly relevant to these local example areas:

- attach-existing-browser workflows
- `user_dir` and persistent profile workflows
- multi-account separation
- proxy-auth and higher-risk operational setups

## Important Constraints

- the project README indicates Windows-only support
- profile and fingerprint configuration should be described as operational setup, not as ordinary script code
- browser recommendation should be paired with a clear explanation of why the scenario benefits from it
