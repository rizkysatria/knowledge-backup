# Canonical Templates

## Test Case Template

Use the user's supplied spreadsheet template whenever available.

### Mobile

Use exactly:
`TC No | Case | Menu / Module | Scenario | Pre-condition | Step | Gherkin | Expected | Actual | Assign Android | Assign iOS | Status Android | Status iOS | Evidence Android | Evidence iOS | Link Jira | Notes`

### Web

Use exactly:
`TC No | Case | Menu / Module | Scenario | Pre-condition | Step | Gherkin | Expected | Actual | Link Jira | Notes`

Rules:
- `Case` uses only `Positive` or `Negative`.
- Expected results are written in Bahasa Indonesia unless explicitly requested otherwise.
- Do not add `Regression UAT`.
- Execution/result fields remain blank for newly generated cases.

## WBS Output Template

For QA Automation WBS, use exactly:

1. Squad
2. Big Feature
3. Epic / Feature
4. Story / Task
5. Sub_task
6. Assignee
7. Status
8. Start Date
9. End Date

Required hierarchy:

`Squad → Big Feature → Epic / Feature → Story / Task → Sub_task`

Typical Story / Task categories when applicable:
- `Development <Feature>`
- `Integration <Feature>`
- `Locator <Feature>`

Rules:
- `Squad` is blank unless explicitly provided.
- Do not invent Assignee, Status, Start Date, or End Date.
- Development is normally decomposed by screen.
- Integration is decomposed by meaningful E2E flow.
- Locator is decomposed by automation-relevant screen/component locator work.
- Do not create one ticket per button or field.

Do not add, remove, rename, reorder, or merge columns unless explicitly requested.

## Agent Task Checklist

### Before work

- [ ] Read `MASTER_INSTRUCTIONS.md`.
- [ ] Identify the task.
- [ ] Identify the source of truth.
- [ ] Load only relevant context.
- [ ] Load relevant skill(s).
- [ ] Load relevant rule(s).
- [ ] Load the required template.

### During work

- [ ] Keep output traceable to source.
- [ ] Avoid unsupported assumptions.
- [ ] Keep responsibilities separated.
- [ ] Preserve requested formats.
- [ ] Keep business behavior separate from implementation details.

### Before delivery

- [ ] Validate completeness.
- [ ] Validate format/schema.
- [ ] Validate IDs/naming where applicable.
- [ ] Validate that no required UI/flow coverage was skipped.
- [ ] Validate generated files exist and open correctly.
- [ ] Leave execution-only fields blank for unexecuted test cases.
