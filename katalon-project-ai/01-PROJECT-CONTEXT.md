# Project Context for AI

Paste this document into an AI conversation before asking it to change this repository.

## What this project is

`ist-automation` is a Katalon Enterprise mobile test-automation project. The core flow is:

```text
Katalon Test Case / Test Suite
  -> Scripts/<Feature>/Script*.groovy
  -> Include/features/<feature>.feature + Cucumber tag
  -> Include/scripts/groovy/features/<feature>/ step/screen/use-case code
  -> Katalon Mobile/Appium + shared keywords/locators/listeners
```

It runs Android and iOS. Platform-specific behavior is commonly controlled by `internal.GlobalVariable.platform` and locator registration in the global listener.

## Important directories

| Path | Role | Change caution |
|---|---|---|
| `Include/features/` | Gherkin scenarios, examples, tags | Tag changes can break scripts/suites. |
| `Include/scripts/groovy/features/` | Feature implementation | Prefer the matching feature package. |
| `Scripts/` | Katalon test-case entry scripts | Usually a thin tag runner. |
| `Test Cases/` | Katalon test-case metadata | Keep scripts and metadata paths aligned. |
| `Test Suites/` | Local/Jenkins/regression orchestration | Changes alter execution coverage/order. |
| `Keywords/` | Shared keywords, DB, reports, utilities | Blast radius can be high. |
| `Test Listeners/` | Global setup/cleanup/recovery | Affects all tests. |
| `Profiles/` | Profile variables/configuration | May contain sensitive environment data. |
| `Include/config/testdata/` | Runtime data pools | Data lifecycle can affect test outcomes. |
| `Data Files/` | Excel source and sync script for pools | Keep Excel and JSON synchronization intact. |

## Test-data contract

Runtime automation reads `Include/config/testdata/pool.json`; the source spreadsheet is `Data Files/TestData.xlsx`. The synchronization script is `Data Files/sync-testdata.py`.

Feature code should obtain data through `PoolReader` and the relevant `<Feature>Pool` accessor. Do not insert raw customer numbers, payment identifiers, PINs, e-mails, or amounts into screens/steps merely to make a test pass. Some payment data can be consumable/rotated, so never casually reorder or replace pools.

## Existing patterns to preserve

* Feature file declares behavior; `Scripts/` chooses the feature and tag.
* UI flow code belongs in the matching `features/<feature>/` package.
* Reusable cross-feature behavior belongs in existing shared layers only when it is genuinely generic.
* Locators are resolved via the existing locator infrastructure, with Android/iOS registrations.
* `GlobalListener` owns cross-test app startup, lifecycle initialization, and recovery. Treat it as high-risk shared code.
* Regression suite entries point to Katalon test-case IDs; verify paths rather than assuming a feature tag automatically has suite coverage.

## Known high-risk areas

* Profiles and configuration may contain confidential values.
* Database helpers can change remote data.
* Payment and other transactional flows can consume test data or create state.
* Global listener, custom keywords, report code, and suites have broad impact.
* Android and iOS may require different locator/gesture paths.

## AI operating request

Inspect the current implementation before proposing code. Do not infer values, selectors, tags, data, or platform behavior. Report uncertainties and ask for the smallest missing evidence rather than guessing.
