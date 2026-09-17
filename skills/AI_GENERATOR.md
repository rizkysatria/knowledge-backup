# AI Automation Generator

## Context

# Context: AI Generator

The AI workflow is intended to transform product and engineering sources into structured QA artifacts.

Typical flow:

`Input → Source Analysis → Feature / Screen Analysis → Plan → Generate → Validate → Output`

For source-driven QA work, maintain traceability between source, feature, test case, and generated artifacts.

The workflow must remain vendor-agnostic and should use repository-local skills, rules, and templates when available.

## Skill

# Skill: AI Automation Generator

Transform product inputs into reusable QA / automation artifacts.

## Workflow

`Input → Context → Skills → Rules → Analyze → Flow Map → Screen Map → Action Map → Expected Behavior Map → State / Validation Map → Plan → Generate → Step Semantic Validation → Coverage Review → Validate → Output`

## Input examples

- User stories
- PRD
- Figma
- SVG
- PDF
- UI screenshots
- API contracts
- Source code

## Principles

- Load relevant context only.
- Apply relevant skills and rules.
- Keep business logic separate from technical implementation.
- Preserve existing templates.
- Validate output before delivery.
- Keep output traceable to the source.
- Do not hardcode project-specific behavior into reusable knowledge.
- Do not generate test cases directly from raw source text without first mapping the user flow and expected behavior.

## Rules

# Rules: AI Generator

- Analyze before generating.
- Load only applicable skills and rules.
- Use current source evidence as the source of truth.
- Keep outputs traceable.
- Do not invent unsupported functionality.
- Do not leak implementation-specific details into business-level Gherkin.
- Validate output against the relevant schema/template before finalizing.

## QA Test Case Generation Rules

Before generating QA test cases, build the following intermediate maps:

1. **Flow Map**
   - Identify the complete user journey from entry point to target business outcome.

2. **Screen Map**
   - Identify relevant screens, sections, and screen states.

3. **Action Map**
   - Identify actions performed by the tester/user.
   - Examples: open, navigate, select, tap, enter data, edit, clear, scroll, swipe, submit, confirm, cancel, authenticate.

4. **Expected Behavior Map**
   - Identify system responses caused by user actions.
   - Examples: screen displayed, validation shown, button state changed, calculation updated, loading displayed, navigation performed, transaction succeeded/failed.

5. **State / Validation Map**
   - Identify resulting UI states, business states, validations, errors, success, failure, retry, and recovery behavior when supported by the source.

Do not generate the final test case directly from raw source text.

## Step / Expected Separation

Use this mapping when generating test cases:

`User Action → Step`

`System Response → Expected`

`Resulting UI / Business State → Expected`

### Step Rules

Every generated Step must:

- Describe an action performed by the tester/user.
- Be executable.
- Follow the actual user journey chronologically.
- Include required navigation to reach the scenario.
- Stay scoped to the scenario.
- Avoid system responses.
- Avoid validation results.
- Avoid verification wording such as `Pastikan`, `Verify`, or `Check`.
- Avoid implementation details, locators, API calls, or technical verification unless explicitly required by the scenario.

### Expected Rules

Every generated Expected must:

- Describe observable system behavior.
- Describe resulting UI or business state when relevant.
- Include validation or error behavior when applicable.
- Not contain tester/user actions.

### Pre-condition Rules

Pre-condition must contain only the state, data, access, configuration, or setup that is already true before execution starts.

Do not put tester actions, navigation, validation, or expected results into Pre-condition.

Do not duplicate the same action or state between Pre-condition and Step.

## Step Semantic Validation

Before finalizing every generated test case, validate the Step.

Check that:

1. The Step is executable by a tester.
2. The Step represents a user/tester action or necessary journey transition.
3. The Step follows chronological order.
4. The Step does not contain system responses as actions.
5. The Step does not contain validation results as actions.
6. The Step does not use `Pastikan`, `Verify`, or `Check` as the primary action.
7. Required navigation is included.
8. The Step does not contain unnecessary micro-steps.
9. The Step is consistent with the source-defined user journey.
10. The Expected contains the corresponding observable system behavior.

If a Step fails validation, rewrite it before final output.

## Negative Test Case Rules

For negative cases, use:

`Navigation / Setup → Invalid User Action or Input → Trigger Action`

Put the resulting validation, error message, blocked outcome, or recovery behavior in Expected.

Example:

```text
Step:
1. Pengguna membuka halaman yang dituju.
2. Pengguna mengisi field dengan data yang tidak valid.
3. Pengguna menekan tombol Lanjut.

Expected:
Sistem menampilkan validasi yang sesuai dan tidak melanjutkan proses selama data tidak memenuhi ketentuan.
```

Do not generate:

```text
Step:
1. Pengguna mengisi data yang tidak valid.
2. Pastikan muncul pesan error.
3. Pastikan proses tidak dilanjutkan.
```

## Test Case Generation

After the intermediate maps are complete:

1. Apply the relevant QA Pack skill and rules.
2. Generate test cases using the applicable template.
3. Keep Pre-condition, Step, and Expected semantically separated.
4. Keep Gherkin aligned with Scenario, Step, and Expected.
5. Do not invent unsupported behavior, limits, validations, or states.
6. Leave execution-only fields blank for unexecuted cases.

## Coverage Review

Perform a second coverage review after initial test case generation.

Compare generated test cases against:

- Source requirements
- Flow Map
- Screen Map
- Action Map
- Expected Behavior Map
- State / Validation Map
- UI inventory
- Navigation paths
- Positive and negative behavior
- Failure and recovery paths

Generate missing test cases when a supported behavior is not covered.

Do not add cases only to increase the test count.

## Final Validation

Before delivery:

- Validate the exact applicable template/schema.
- Validate Pre-condition vs Step separation.
- Validate Step vs Expected separation.
- Run Step Semantic Validation for every test case.
- Validate Gherkin alignment.
- Validate source traceability.
- Validate that no unsupported behavior has been introduced.
- Perform the second coverage review.
- Leave execution-only fields blank unless actual execution evidence exists.

## QA Pack Alignment

For QA artifact generation:

- Treat the current requirement/design/application source as the source of truth.
- Load only the relevant QA Pack context, skill, rules, and template.
- For test cases, apply `QA_TEST_CASE_GENERATION.md` and `TEMPLATES.md`.
- For Figma/SVG WBS, apply `FIGMA_WBS.md` and `TEMPLATES.md`.
- Validate generated output against the applicable schema before delivery.

Do not use an existing artifact as a hidden template for content unless the user explicitly requests conformance to it.
