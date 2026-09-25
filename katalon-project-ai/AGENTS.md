# Repository Instructions: ist-automation

## Purpose and stack

This is a Katalon Enterprise mobile-automation project. Test implementation uses Groovy, Appium/Katalon Mobile keywords, Cucumber feature files, Katalon test cases, and Katalon test suites. It supports Android and iOS execution profiles.

## Before editing

1. Read this file, then inspect the target feature file, its step definitions, screen/use-case classes, and the Katalon script that invokes the tag.
2. State the files you expect to modify and why before making a change.
3. Check `git status --short`. Treat existing changed/untracked files as user work; do not overwrite, revert, format, or include them unless explicitly asked.
4. Make the smallest change that satisfies the request. Do not refactor unrelated code.

## Architecture and ownership

* `Include/features/*.feature`: Gherkin scenarios and tags.
* `Include/scripts/groovy/features/<feature>/`: step definitions, screens, use cases, and feature-specific test-data accessors.
* `Scripts/<Feature>/`: Katalon test-case scripts; typically execute a feature file with one or more Cucumber tags.
* `Test Cases/`: Katalon test-case metadata. `Test Suites/`: local, Jenkins, and regression collections.
* `Keywords/`: reusable Katalon custom keywords, database helpers, reporting, and utility code.
* `Test Listeners/GlobalListener.groovy`: lifecycle setup/recovery; changes here affect every test.
* `Profiles/*.glbl`: execution variables and potentially sensitive configuration.
* `Include/config/testdata/pool.json`: runtime test-data source. `Data Files/TestData.xlsx` is synchronized to it by `Data Files/sync-testdata.py`.

## Mandatory safety rules

* Never print, copy to chat, commit, or replace secrets, credentials, account identifiers, tokens, database settings, or device IDs. Redact them in all reports.
* Do not edit a profile, listener, Gradle configuration, shared custom keyword, test-data pool, Excel source, or test suite unless the request explicitly requires it.
* Do not hardcode business test data in screen or step classes. Follow the existing `PoolReader` and feature `<Feature>Pool` accessor pattern.
* Preserve Android/iOS behavior. Any UI flow change must inspect existing `GlobalVariable.platform` branches and say whether both platforms are covered.
* Reuse the repository's locator registry/resolver and existing feature conventions. Do not invent locator keys or selector values without an inspected source or supplied evidence.
* Do not use destructive git commands, bulk renames, broad formatting, or dependency upgrades unless explicitly requested.

## Change workflow

1. Inspect and summarize the current flow and the exact affected tag(s).
2. Propose a minimal file list and acceptance criteria.
3. Implement only after the scope is clear.
4. Show changed files, behavioral impact, risks, and validation performed.
5. If Katalon/device execution is unavailable, say so clearly; do not claim tests passed.

## Quality expectations

* Keep Gherkin readable and tags stable.
* Keep test-case scripts thin; put UI behavior in the matching feature package.
* Use explicit assertions/waits appropriate to the existing style; avoid arbitrary sleeps when an existing wait or recovery helper fits.
* Keep positive and negative scenario behavior isolated where the current feature separates them.
* Avoid changing a shared utility as a shortcut for a feature-specific problem.

## Required final report format

Use this concise structure:

1. **Changed:** files and purpose.
2. **Behavior:** scenario/tag/platform effect.
3. **Validation:** commands or execution actually run, with result.
4. **Not validated / risk:** anything requiring a device, test data, profile, or manual confirmation.
