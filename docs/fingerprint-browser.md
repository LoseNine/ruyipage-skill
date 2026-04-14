# Fingerprint Browser

## Official Project

- <https://github.com/LoseNine/firefox-fingerprintBrowser>

## When To Use It

Use it when:

- the site is under risk control or anti-bot pressure
- persistent identity matters
- fingerprint consistency matters
- multiple accounts require stronger separation

## Default Path Assumption

This skill assumes that the Firefox browser installed under the default Windows `C` drive path is the fingerprint browser.

If that is not true in the actual environment, detect the real browser path before continuing.

## Consistency Rules

Keep these aligned with the effective IP context and with each other:

- WebRTC
- language / locale
- timezone
- geolocation
- speech
- other fingerprint surfaces

Do not mix unrelated identity traits in one profile.

## Profile Rule

- prefer a fresh `user_dir` for a new identity
- reuse an existing `user_dir` only when the workflow explicitly depends on persisted state
