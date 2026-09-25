# Prompt Templates

Replace every `[placeholder]`. Attach only redacted logs/screenshots and the smallest relevant files.

## 1. Analysis only (recommended first prompt)

```text
You are analyzing the Katalon mobile automation repository `ist-automation`.
Read the repository instructions and do not edit files yet.

Goal: [describe one concrete failing behavior or requested change].
Known scope: [feature/tag/test-case path/platform].
Evidence: [redacted error, log excerpt, screenshot, or ticket acceptance criteria].

Trace the current execution path from test case/script to feature tag, step definitions, screen/use-case code, locator/data dependencies, and platform branches. Return:
1. current behavior and likely cause, citing files;
2. unknowns that require evidence (do not guess);
3. the minimal proposed file list;
4. acceptance criteria and a safe validation plan.
Do not modify code, profiles, test data, suites, listeners, or shared utilities.
```

## 2. Minimal bug fix

```text
Implement only the approved fix below in `ist-automation`.

Problem: [one bug].
Approved behavior: [what must happen].
In scope: [exact files or feature/tag].
Out of scope: profiles, test data, suites, global listener, shared keywords, refactoring, formatting, dependencies.
Platforms: [Android/iOS/both].
Evidence: [redacted evidence].

Before editing, restate the call path and files you will touch. Preserve existing project conventions and both platform branches. Do not invent locators, tags, or test data. After editing, report changed files, behavior impact, validation actually run, and risks not validated.
```

## 3. Add one scenario/tag

```text
Add one narrowly scoped scenario for [business flow] in `ist-automation`.

Feature: [feature file].
New tag: [tag name].
Platform coverage: [Android/iOS/both].
Acceptance criteria: [observable Given/When/Then behavior].
Test data source/accessor already approved: [accessor name, or “unknown—analyze only”].

First inspect an equivalent existing scenario and show the minimal files required: feature, implementation, Katalon script/test case, and suite only if explicitly needed. Reuse existing locators and data accessors; do not hardcode sensitive/business data. Do not edit global/shared infrastructure. Stop if a locator, data pool, or expected result is not evidenced.
```

## 4. Code review / PR review

```text
Review this diff for `ist-automation`; do not modify files.

Intended outcome: [ticket/acceptance criteria].
Changed files: [list or diff].
Platforms: [Android/iOS/both].

Check for: wrong tag/script wiring, broken Katalon paths, Android/iOS regression, invented/missing locator keys, hardcoded test data, data-pool lifecycle risk, shared-code blast radius, missing assertions/waits, profile/secret exposure, and unvalidated assumptions. Report only actionable findings ranked Critical/High/Medium/Low, each with file and rationale. State explicitly if validation cannot be inferred.
```

## 5. Failure triage from a run

```text
Analyze this failed automated test without editing code.

Test case/tag: [path and tag].
Platform/profile: [redacted profile name and device type].
Failure point: [step/UI state].
Redacted logs: [excerpt].
Relevant screenshot/UI hierarchy: [attachment if allowed].

Trace the likely flow and provide ranked hypotheses with supporting code references. Separate confirmed facts from hypotheses. Specify the smallest next diagnostic action for each hypothesis. Do not recommend changing locators, waits, test data, or profiles without evidence.
```
