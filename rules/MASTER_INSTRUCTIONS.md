# QA Engineering — Master Instructions

## Purpose

This is the master instruction set for the reusable QA Engineering Knowledge Base.

Read this file first, then load only the materials relevant to the current task.

The knowledge base supports:
- QA test case generation
- QA automation planning and implementation
- Figma / SVG to WBS generation for QA Automation
- Mobile automation
- CI/CD
- Reporting / log analysis
- Documentation / handover
- AI-assisted source-to-artifact workflows

---

## 1. Core Operating Flow

For every task:

`Identify Task → Identify Source of Truth → Load Relevant Context → Load Relevant Skill(s) → Load Relevant Rule(s) → Load Template → Analyze → Generate → Validate → Output`

Do not load or apply unrelated project knowledge.

---

## 2. Knowledge Base Layers

Keep responsibilities conceptually separated:

- `Context` = background knowledge and established technical context
- `Skill` = how to perform a task
- `Rules` = mandatory constraints, standards, and quality gates
- `Template` = required output structure

Do not turn project-specific observations into global reusable rules unless explicitly established as reusable.

---

## 3. Source of Truth

Use this precedence when information conflicts:

1. Explicit current user instruction
2. Current task source / requirement / design / application behavior
3. Applicable project context explicitly supplied for the task
4. QA Knowledge Base
5. Generic domain assumptions

Never use a generic assumption to override explicit source evidence.

Do not invent:
- Requirements
- UI behavior
- Business rules
- Exact validation limits
- Screens
- User flows
- Test results
- Evidence
- Assignees
- Dates
- Statuses
- Implementation details

When information is unavailable, keep it unknown or requirement-dependent.

---

## 4. Test Case Generation

For test-case tasks, load:

- `QA_TEST_CASE_GENERATION.md`
- `CREATE_TEST_CASE_RULES.md` when the task is explicitly to create/generate test cases
- `TEMPLATES.md`
- Relevant source material such as PRD, User Story, Figma, SVG, screenshot, API contract, or observed application behavior

### Mandatory approach

Analyze the complete user journey before generating test cases:

`Source → User Journey → UI / Interaction Map → Test Scenarios → Test Cases → Validation`

Then perform a second review:

`Generated Test Cases → UI Inventory → User Flow → Gap Detection → Missing Cases`

Do not consider the test set complete until the second coverage review is performed.

### Current test-case conventions

- `Case` = `Positive` or `Negative`
- Do not add `Regression UAT` unless the user explicitly requests it
- Expected Result = Bahasa Indonesia unless explicitly requested otherwise
- Pre-condition = state/data/setup already true before execution
- Step = chronological tester actions starting from the applicable journey entry point, including all required navigation/actions through the target scenario outcome
- Step must be executable without the tester guessing how to reach the target screen
- Do not shortcut or omit source-defined navigation
- Expected = observable system result/behavior caused by the actions in Step
- Pre-condition contains only state/data/setup already true before execution
- Do not duplicate the same state/action between Pre-condition and Step
- Preserve the supplied test-case template exactly

### UI coverage

For UI-driven features, inventory every relevant visible and interactive element and account for:
- Actions
- Validation
- State changes
- Navigation
- Loading
- Success/failure
- Retry/recovery
- Back/cancel/close
- Alternate paths
- Meaningful combinations and dependencies

Do not stop coverage at the first successful screen when the business flow continues.

---

## 5. Figma / SVG to WBS

For WBS tasks, the WBS is specifically for QA Automation planning unless the user states otherwise.

Load:

- `FIGMA_WBS.md`
- `TEMPLATES.md`
- Relevant PRD / User Story / Figma / SVG / screenshots

### Mandatory hierarchy

`Squad → Big Feature → Epic / Feature → Story / Task → Sub_task`

### Current WBS schema

`Squad | Big Feature | Epic / Feature | Story / Task | Sub_task | Assignee | Status | Start Date | End Date`

### Decomposition

When applicable:

`Development <Feature>`
→ `Automation Screen <Screen Name>`

`Integration <Feature>`
→ `Gherkin Integration <Meaningful E2E Flow>`

`Locator <Feature>`
→ `Object ID <Screen / Component>`

Development is normally screen-based.

Integration represents meaningful end-to-end business flows.

Locator represents automation-relevant locator work.

Do not create one ticket per button or field by default.

### Critical WBS rule

Generate the WBS from the current source.

Do not copy an existing WBS as content unless the user explicitly asks for conformance to that WBS.

Existing WBS examples may be used only as structural/template references when appropriate.

### Metadata

Do not infer:
- Squad
- Assignee
- Status
- Start Date
- End Date

Leave them blank when unsupported by the source.

### Variants

Create separate screen or flow items only when the source provides evidence that they represent meaningful distinct automation work.

Do not silently omit meaningful source-defined variants.

---

## 6. Automation Architecture

When working on automation architecture or implementation, load:

- `AUTOMATION.md`
- `MOBILE_AUTOMATION.md` for mobile work
- Relevant naming/output rules

Established architecture:

`Feature → Step Definition → Usecase → Screen → Katalon/Appium → Device`

Keep responsibilities separated.

Prefer solving changes at the narrowest responsible layer.

---

## 7. Mobile Automation

For Android/iOS automation, load `MOBILE_AUTOMATION.md`.

Prefer:
- Android: stable `resource-id`
- iOS: stable `accessibility-id`

Avoid fragile or absolute XPath when stable identifiers are available.

Prefer condition-based waits over fixed sleeps.

Verify device, Appium, app state, locator, synchronization, and gesture/input behavior before changing shared framework code.

---

## 8. Jenkins / CI/CD

For CI/CD tasks, load `JENKINS_CI_CD.md`.

Keep environment-specific configuration parameterized/configurable.

Never hardcode credentials or secrets.

Validate device/application readiness before execution.

Keep infrastructure/environment failures distinguishable from actual test failures.

---

## 9. Reporting / Log Analysis

For reporting tasks, load `REPORTING.md`.

Calculate metrics only from actual execution evidence.

Keep parsing, normalization, mapping, calculation, and presentation logically separated.

Never fabricate:
- Pass rate
- Failure rate
- Flaky rate
- Test counts
- Execution results

Distinguish test failures from parsing, infrastructure, or environment failures.

---

## 10. Documentation

For documentation or handover tasks, load `DOCUMENTATION.md`.

Preserve factual accuracy.

Do not invent architecture, tools, dependencies, or requirements.

For formatting-only requests, preserve the document's wording, meaning, structure, and data.

---

## 11. AI-Assisted Generation

For source-to-artifact workflows, load `AI_GENERATOR.md`.

Use:

`Input → Context → Skills → Rules → Analyze → Plan → Generate → Validate → Output`

Always keep generated artifacts traceable to their source.

Do not use an existing artifact as a hidden content template unless the user explicitly requests conformance.

---

## 12. Output and Template Rules

When a template is supplied:

- Preserve its exact column/field order
- Do not add or remove fields unless explicitly requested
- Keep execution-only fields blank for unexecuted cases
- Validate the generated output against the required schema
- Ensure generated files are readable and usable

Use `NAMING_AND_OUTPUT.md` for naming and file-output conventions.

---

## 13. Final Quality Gate

Before delivery, verify:

- The correct source of truth was used
- Only relevant knowledge-base materials were applied
- No unsupported requirements or behavior were invented
- The requested template/schema was preserved
- Coverage is complete for the task type
- Output is traceable to the source
- Metadata was not guessed
- Execution results/evidence were not fabricated
- Generated files exist and are readable

For Test Case Generation:
- Apply `CREATE_TEST_CASE_RULES.md` when the task is explicitly create-test-case generation.
- Validate `Entry Point → Full Required Journey → Target Action → Expected Outcome`.
- Run the required two-pass coverage review.

For WBS Generation:
- Verify source-derived screens, meaningful variants, E2E flows, locator work, hierarchy, and metadata.

---

## 14. Maintenance Rule

When a canonical rule or template changes, update all dependent knowledge-base files that reference it.

Avoid duplicate or contradictory rules.

Prefer one canonical definition with lightweight references from dependent files.

The QA Pack should remain internally consistent across:
- `MASTER_INSTRUCTIONS.md`
- `QA_TEST_CASE_GENERATION.md`
- `FIGMA_WBS.md`
- `TEMPLATES.md`
- `README.md`
- Other task-specific context/skill/rule files
