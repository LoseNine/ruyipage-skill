# Anti-Hallucination Rules

Use these rules whenever producing `ruyiPage` guidance.

## API Grounding

- Do not invent methods, classes, or parameters that are not grounded in local examples, references, or source code.
- Prefer naming the example file that supports the suggested pattern.
- If a supported example exists, prefer using that path over listing unsupported possibilities.

## Standard Versus Implementation

- Do not claim that a W3C WebDriver BiDi command is exposed by `ruyiPage` unless the repository evidence supports it.
- Do not describe a `ruyiPage` convenience method as if it were the raw W3C command unless the distinction is made clear.

## Environment Sensitivity

- Do not generalize from a real-site example to all websites.
- Do not imply that anti-bot resilience is guaranteed by default.
- Recommend the official fingerprint browser only when the workflow benefits from it.
- When a site is environment-sensitive, bound the claim narrowly and continue with the closest supported workflow instead of treating the whole task as blocked.

## Comprehensive Analysis Claims

- If the user asks for webpage-parameter analysis, do not claim the result is comprehensive unless page readiness, page source, JS/runtime clues, and browser-observable network traffic were all considered.
- Distinguish rendered DOM, runtime state, and browser-observable network traffic rather than collapsing them into one vague notion of "source".

## Escalation Discipline

- Start with simple examples and high-level APIs.
- Escalate to advanced BiDi, interception, script internals, or fingerprint-browser workflows only when the task requires them.
- If recommending a JS interaction route, do not imply that one event is enough. Name or describe the full event sequence the target control expects, and mention `ruyi: true` when that is part of the intended fidelity.
- If one exact approach is not grounded, propose the nearest grounded alternative rather than stopping at a general refusal.
