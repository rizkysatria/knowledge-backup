# Safe AI Change Rules

Use these rules in every prompt that asks AI to edit the repository.

## Scope control

* Start with analysis. Ask AI to name the current call path, affected tag(s), and proposed files before editing.
* Give one small outcome per request: for example, “fix the Android wait for tag X,” not “clean up payment automation.”
* Require the smallest viable diff. No opportunistic refactor, cleanup, rename, formatting pass, or dependency change.
* Keep untracked and pre-existing modified files out of scope.

## Never let AI guess

AI must inspect or receive evidence for:

* Cucumber tag names and feature scenario structure.
* Locator keys and Android/iOS locator implementations.
* Runtime test-data pool/accessor names.
* Test-case IDs and suite membership.
* Required profile variables and device behavior.
* Expected UI text, error state, or business rule.

If any item is unknown, AI must say `unknown`, explain the impact, and request the exact file/log/screenshot needed.

## Sensitive-data boundary

Never paste raw content from `Profiles/`, test-data pools, spreadsheets, test reports, device logs, or DB query outputs into a public AI service. Redact credentials, account numbers, access IDs, phone numbers, e-mails, tokens, IPs, database URLs, and personal data.

AI must not add secrets to source, fixtures, comments, screenshots, commit messages, or documentation. Use placeholders such as `<REDACTED_ACCOUNT>` when discussing examples.

## Katalon/mobile guardrails

* Preserve both Android and iOS paths unless the ticket expressly targets one platform.
* Prefer existing locator, screen, use-case, recovery, and test-data helpers.
* Do not replace a specific wait/assertion with `Thread.sleep` unless the existing codebase has no viable synchronization point and the reason is documented.
* Do not change `GlobalListener`, profiles, database code, report code, shared keywords, or suites for a feature-only ticket.
* Do not alter data pools or run a state-changing test without human confirmation of environment and test-data impact.

## Required AI response gates

Before code: current behavior, proposed files, acceptance criteria, uncertainty.

After code: exact changed files, tags/scenarios/platforms affected, validation actually run, and remaining risk. “Should work” is not a validation result.

## Stop-and-escalate conditions

AI must stop and ask for direction when the task requires a new credential, production-like data, a new locator value without source evidence, a database mutation, a profile change, broad refactor, dependency upgrade, suite reordering, or a choice between materially different behaviors.
