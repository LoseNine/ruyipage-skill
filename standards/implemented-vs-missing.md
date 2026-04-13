# Implemented Vs Missing

This summary is based on the local comparison assets under `E:\ruyipage\examples\w3c_bidi`.

## Standard Totals

- W3C commands: 63
- W3C events: 24

## Purpose Of This Document

This file exists so an AI can avoid overclaiming support.

Use it to distinguish between:

- present in W3C BiDi
- implemented in `ruyiPage`
- implemented but not strongly covered in local example validation

## Current Coverage Notes

- `session`, `network`, `script`, `storage`, and `input` are strongly represented in local comparison data
- some `browsingContext`, `emulation`, and event surfaces have partial or caveat-heavy coverage
- not every W3C event listed in the standard is treated as first-class in local examples

## AI Guidance

- do not state that every W3C module surface is fully exposed just because it exists in the standard
- prefer local examples as evidence of practical support
- use this file and the comparison references to explain partial implementation or partial test coverage
