# Human Checklist Before Running or Merging AI Changes

## Scope and repository safety

- [ ] The ticket has one clear, observable outcome.
- [ ] `git status --short` was checked; unrelated local work was preserved.
- [ ] The diff contains only expected files and no broad formatting/refactor.
- [ ] No generated output, report, cache, local state, or IDE file is included.
- [ ] No credential, account identifier, device identifier, personal data, token, or connection detail appears in the diff or AI chat transcript.

## Katalon flow correctness

- [ ] The feature tag exists and matches the script that invokes it.
- [ ] The Gherkin scenario, examples, and step definitions match exactly.
- [ ] The Katalon test-case path remains valid.
- [ ] If a suite changed, its test-case IDs and intended run order were manually checked.
- [ ] New UI behavior is implemented in the correct feature package, not accidentally in a global listener or shared utility.

## Platform, locators, and data

- [ ] Android and iOS implications were reviewed; platform-specific code was preserved or intentionally changed.
- [ ] Every locator key/selector comes from a verified existing source or a reviewed new locator definition.
- [ ] No raw business test data was hardcoded in a screen or step.
- [ ] Test data uses the approved feature pool/accessor pattern.
- [ ] Any transactional/consumable data impact is understood before execution.

## Validation and handoff

- [ ] The exact changed tag or test case was executed in the intended safe environment, or the reason it could not be run is recorded.
- [ ] Relevant negative/adjacent flow was considered when behavior is shared.
- [ ] The result distinguishes “executed and passed” from “not executed.”
- [ ] Known limitations, device requirements, and follow-up work are documented in the PR/ticket.

## Fast final question

Before merge, ask: “Can we point to evidence for every new tag, locator, data accessor, platform branch, and expected assertion?” If not, do not merge until the missing item is verified.
