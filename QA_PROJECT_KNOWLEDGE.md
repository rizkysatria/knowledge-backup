# QA_PROJECT_KNOWLEDGE

> Consolidated Project Knowledge for QA Test Case / Automation workflow.
> This file preserves the supplied QA Pack source documents as distinct sections for traceability.
> Source order: MASTER_INSTRUCTIONS, CREATE_TEST_CASE_RULES, QA_TEST_CASE_GENERATION, AI_GENERATOR, AUTOMATION, MOBILE_AUTOMATION, FIGMA_WBS, TEMPLATES, NAMING_AND_OUTPUT, DOCUMENTATION, README, UPDATE_MANIFEST.


---

# SOURCE: MASTER_INSTRUCTIONS.md

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


---

# SOURCE: CREATE_TEST_CASE_RULES.md

# Create Test Case Rules

## Purpose

Define the mandatory behavior when generating QA test cases from a provided source.

## Core Rule

When the user asks to create test cases, use the QA Pack as the governing rules and use the provided source as the source of truth for requirements, UI, flow, validation, and behavior.

Do not invent unsupported requirements, UI behavior, business rules, validation limits, screens, navigation, test results, evidence, metadata, or implementation details.

## Generation Flow

Always follow:

`Source → User Journey → UI / Interaction Map → Test Scenarios → Test Cases → Validation`

For each test case:

`Entry Point → Full Required Journey → Target Action → Expected Outcome`

## Step Rules

Step must:

- Start from the applicable journey entry point.
- Include every required navigation and user action needed to reach the target scenario.
- Continue through the action that triggers the scenario outcome.
- Be chronological and executable by another tester without guessing.
- Describe tester/user actions only.

Do not:

- Jump directly to the target screen when navigation is part of the source-defined journey.
- Use shortcuts such as `Open target screen`, `Navigate to confirmation`, or equivalent when the actual journey is known.
- Put system responses, validation results, or expected outcomes into Step.
- Use `Pastikan`, `Verify`, or `Check` as the primary Step action.
- Add unnecessary micro-steps when a meaningful combined action is sufficient.

## Pre-condition Rules

Pre-condition contains only state, data, access, configuration, or setup that is already true before execution starts.

Do not use Pre-condition to hide required user navigation or actions that belong in the test journey.

## Expected Rules

Expected must describe the observable system result caused by the actions in Step.

Expected may describe:

- Validation or error message
- UI state change
- Button state change
- Calculation result
- Navigation result
- Loading / success / failure behavior
- Business outcome

For negative cases, Expected should clearly state the validation/error and the outcome that must not proceed when supported by the source.

Expected must not become a repetition of Step.

Expected Result must be written in Bahasa Indonesia unless explicitly requested otherwise.

## Coverage Rules

Analyze the complete source-defined journey before generating cases.

Cover relevant:

- Positive and negative scenarios
- Required-field and invalid-input validation
- Supported boundary values
- Navigation and state transitions
- Alternate paths
- Failure and recovery
- Back / cancel / close behavior
- Meaningful end-to-end business flows
- Security, UX, compatibility, API, or DB behavior when supported and relevant

Do not invent boundary values when the source does not define them.

Do not create redundant micro-cases only to increase test-case count.

## Template Rules

Use the applicable QA Pack template exactly.

Do not add, remove, rename, or reorder columns unless explicitly requested.

For unexecuted test cases, keep execution-only fields blank.

## Gherkin Rules

Gherkin must remain aligned with Scenario, Step, and Expected.

Describe behavior, not implementation details.

## Validation Before Delivery

For every generated test case, verify:

1. The entry point is correct.
2. The Step contains the full required journey.
3. No required navigation was skipped.
4. The target action is present.
5. Expected describes the resulting system behavior.
6. Pre-condition and Step are not duplicating each other.
7. No unsupported behavior was introduced.
8. The applicable template/schema is preserved.
9. A second coverage review has been performed against the source-defined journey and UI/interaction coverage.

## Canonical Example

Scenario:
`Nominal Target di bawah minimum`

Pre-condition:
`Nasabah memiliki akun terverifikasi.`

Step:
1. Buka aplikasi.
2. Login menggunakan akun yang terverifikasi.
3. Pilih menu Tabungan Rencana.
4. Pilih `Mulai Sekarang`.
5. Centang checkbox S&K.
6. Tekan `Lanjut`.
7. Pilih `Konvensional`.
8. Tekan `Lanjut`.
9. Pilih tujuan `Edukasi`.
10. Tekan `Lanjut`.
11. Pilih `Menabung dengan target`.
12. Tekan `Lanjut`.
13. Masukkan Nominal Target di bawah minimum yang ditentukan source.
14. Tekan `Lanjut`.

Expected:
`Sistem menampilkan pesan validasi bahwa Nominal Target berada di bawah minimum dan proses tidak dapat dilanjutkan.`

The example demonstrates the required separation:
`Pre-condition = existing state`
`Step = complete tester journey`
`Expected = observable system outcome`


---

# SOURCE: QA_TEST_CASE_GENERATION.md

# QA Test Case Generation


## Skill

# Skill: QA Test Case Generation

## Purpose

Generate production-ready QA test cases from verified requirements, UI/source material, designs, API contracts, or application behavior.

The output should be detailed enough for manual QA execution, UAT, regression, automation planning, and relevant security validation.

## 1. Core Principle

Test cases must be derived systematically and comprehensively from the actual functionality of the system.

For UI-based features, do not stop at happy path, negative, or security cases. Every visible UI element, input, control, interaction, state, validation, transition, and navigation path must be considered for functional coverage.

The test case generation process must follow the actual user journey from entry point to completion, including alternative paths, validation failures, retries, back navigation, state changes, and recovery flows.

The goal is to produce detailed test cases with minimal skipped functionality or untested user interactions.

## 2. Mandatory Coverage Approach

Before generating test cases:

1. Identify the complete user flow from entry point to exit point.
2. Break the flow into every screen, section, step, and user action.
3. Inventory every visible and interactive UI element on each screen.
4. Identify the expected behavior for each interaction.
5. Identify state changes caused by each action.
6. Identify validation, error handling, loading, success, and failure behavior.
7. Identify alternate paths and conditions that can change the flow.
8. Identify dependencies between fields, controls, screens, and actions.
9. Trace each flow until the expected end state is reached.

Do not generate test cases only from high-level requirements. When UI/source material is available, use the actual UI and user interaction flow as the primary coverage map.

## 3. Flow-Complete Rule

A test flow is not complete simply because the primary action succeeds.

For each meaningful action, consider:

`Action → System Response → UI State Change → Next Available Action → Alternate Outcome → Recovery Path → Final Expected State`

Example:

`Open Screen → Enter Data → Submit → Validation → Loading → Success / Failure → UI State Change → Navigation → Next Action → Final Result`

## 4. UI Element Coverage

For each screen, account for all relevant:

- Text inputs
- Password inputs
- Dropdowns / selects
- Radio buttons
- Checkboxes
- Date pickers
- File uploads
- Buttons
- Links
- Back / close / cancel actions
- Tabs
- Search / filter / sort controls
- Expand / collapse controls
- Dialogs
- Toasts / snackbars
- Loading indicators
- Error / success messages
- Scrollable sections
- Sticky or fixed actions

An interactive element should have functional behavior coverage. Do not treat an element as covered merely because it appears in a screenshot.

## 5. Interaction Depth

For each interactive element, consider:

- Initial state
- Primary interaction
- Result of interaction
- State after interaction
- Repeated interaction
- Change / reselection
- Invalid interaction
- Interaction after a previous error
- Interaction after a previous success
- Interaction in combination with other controls
- Impact on the next step

## 6. Functional UI Coverage

Where applicable, test:

### Navigation
- Entry point
- Next / continue
- Back
- Cancel
- Close
- Redirect after success
- Redirect after failure
- Refresh / reload behavior on web

### Inputs
- Empty
- Valid value
- Invalid format
- Special characters
- Whitespace
- Leading / trailing whitespace
- Boundary lengths or values
- Paste / replacement behavior where relevant
- Keyboard / input mode where relevant
- Error state and recovery

### Controls
- Default state
- Select / deselect
- Reselect / change value
- Disabled state
- Enabled state
- Visibility changes

### State and feedback
- Loading
- Disabled while processing
- Inline validation
- Error message
- Success message
- Retry
- Recovery
- Data retained after validation failure

## 7. End-to-End Completion

For flows spanning multiple screens, follow the journey until the actual business outcome is reached.

Do not stop at the first successful screen.

A meaningful flow may be:

`Entry → Input → Validation → Confirmation → Authentication → Result → Final Outcome`

The actual sequence must come from the supplied source.

## 8. Negative and Boundary Coverage

For important fields and actions, consider:

- Missing required data
- Invalid input
- Invalid combinations
- Minimum / maximum boundaries
- Just below / at / just above boundaries
- Wrong format
- Repeated action
- Duplicate submission
- Failure and retry
- Unexpected state

Do not invent exact limits when the requirement does not define them.

## 9. Security / Abuse / Data Integrity

Where relevant, consider:

- XSS / HTML injection
- SQL injection
- Parameter tampering
- Authentication / authorization issues
- Duplicate / replay behavior
- Rate limiting / abuse
- Sensitive data exposure
- File upload abuse
- Session handling
- CSRF
- Transport security

Security cases should be authorized and appropriate to the environment.

## 10. UX / Compatibility

Where relevant, consider:

- Focus behavior
- Keyboard navigation
- Touch behavior
- Accessibility labels
- Readability
- Responsive layout
- Supported browsers / devices
- Orientation
- Mobile keyboard behavior

## 11. API / DB

When the feature exposes API or DB behavior, consider:

- Request payload
- Response mapping
- Server-side validation
- Error handling
- Persistence
- Data consistency
- Tampering

API / DB validation complements UI testing; it does not replace functional UI coverage.

## 12. Two-Pass Coverage Review

### Pass 1 — Generate

`Source → Flow Map → UI Inventory → Interaction Map → State Map → Test Cases`

### Pass 2 — Review

`Generated Test Cases → Compare Against UI Inventory → Compare Against User Flow → Detect Gaps → Generate Missing Test Cases`

Do not consider the task complete until Pass 2 has been performed.

## 13. Quality Gate

Before finalizing, verify:

- Every relevant screen is covered.
- Every relevant interactive UI element is accounted for.
- Every major navigation path is covered.
- Success, failure, retry, and recovery paths are covered where applicable.
- Validation and state transitions are covered.
- Relevant negative and boundary cases exist.
- Security / UX / compatibility / API coverage is included where relevant.
- No unsupported behavior has been invented.
- Test cases are detailed enough to execute without guessing.

## 14. Output Principle

The objective is not maximum test-case count.

The objective is complete, meaningful, risk-based coverage with minimal skipped functionality, while avoiding redundant micro-cases.


## Rules

# Rules: QA Test Case Generation

## 1. Template

Use the user's existing template exactly when one is provided. Do not change column order, headers, spacer columns, assignments, execution fields, or evidence fields unless explicitly requested.

## 2. Coverage

Do not generate only happy-path cases. Functional UI coverage is mandatory for relevant UI-driven features.

Before finalizing:
- Inventory screens.
- Inventory interactive elements.
- Map user interactions.
- Map states and transitions.
- Map validation and failure handling.
- Map navigation and recovery.
- Compare generated test cases against the inventory and flow.

## 3. No-Skip Rule

A relevant interactive UI element must be accounted for. Simple, optional, secondary, or visually minor controls must not be silently skipped when they can affect user behavior or system state.

## 4. Actionable Negative Cases

Every negative case must identify:
1. What is invalid.
2. What action is performed.
3. What should happen.
4. What must not happen.

## 5. Boundary

When limits exist, cover around the boundary. Never invent an exact limit that is not supported by the requirement/source.

## 6. Expected Result

Expected results must be observable and testable. Avoid vague statements such as `System works correctly.`

## 7. Independence

Keep test cases independent where practical. Document unavoidable dependencies in Pre-condition or Notes.

## 8. Gherkin

Gherkin must stay aligned with Scenario, Step, and Expected. Gherkin should express behavior, not implementation details.

## 9. Security

Security testing must be authorized and relevant to the feature. Do not add irrelevant cases only to inflate count.

## 10. Execution Fields

For newly generated cases, leave Actual, Status, Evidence, and Jira execution/result fields blank. Never mark a case as Passed without execution evidence.

## 11. Case Classification

Use only:
- `Positive`
- `Negative`

Do not add other case classifications unless explicitly requested.

## 12. Pre-condition vs Step

Keep Pre-condition and Step clearly separated.

### Pre-condition
Describe the state, data, access, configuration, or setup that must already be true before execution starts.

## Pre-condition Construction Contract

Pre-condition describes only what is already true before Step 1 starts.

Pre-condition must not contain:
- Tester actions
- Navigation actions
- Validation actions
- Expected results
- Actions that are repeated in Step

Use Pre-condition for:
- Account/access state
- Required test data
- Existing account/product state
- Required environment/configuration state
- Required previous business state

If a state can be reached by normal user interaction in the scenario,
prefer putting the navigation/action in Step rather than hiding it in
Pre-condition.

Example:

Bad:
Pre-condition:
"Nasabah sudah berada di halaman Tentukan Target dan Periode dan sudah
memilih Menabung dengan Target."

Step:
"Isi Nama Tabungan..."

Better when the journey is part of the scenario:

Pre-condition:
"Nasabah sudah login dan memiliki akses ke Tabungan Rencana."

Step:
1. Pengguna memilih Tabungan Rencana
2. Pengguna memilih tujuan menabung
3. Pengguna memilih Menabung dengan Target
4. Pengguna mengisi Nama Tabungan
...

### Step
Describe the actions performed by the tester from the applicable entry point through the target business outcome.

Do not duplicate the same action or state in both fields.

### Step Writing Style

Step should be written as a **user journey sequence**, from the applicable entry point to the target business outcome.

Use short, chronological, executable actions that describe what the tester/user does in the flow.

Preferred style:
- Start from the applicable entry point.
- Use one action or meaningful journey transition per numbered step.
- Keep the wording consistent, for example: `Pengguna memilih ...`, `Pengguna mengisi ...`, `Pengguna menekan ...`, `Pengguna melakukan ...`.
- It is acceptable to include a direct journey state when it helps establish where the user is before the next action, for example: `Pengguna berada di halaman ...`.
- Include the necessary navigation steps that lead to the scenario under test.
- For an end-to-end scenario, continue the sequence until the target business outcome is reached.
- Keep validation messages, system responses, UI state results, and other observations in **Expected**, not as the main content of Step.
- Do not write implementation details, locator details, API calls, or technical verification steps unless the test scenario explicitly requires them.
- Do not make every field interaction into a separate micro-step when a form can be represented as one meaningful user action.


## Step Construction Contract

Every Step must represent an executable tester/user action or an explicit
journey position required to perform the next action.

Step must answer:
"What does the tester/user do?"

Expected must answer:
"What does the system show/do as a result?"

### Allowed Step Content

Step may contain:
- Open / launch application
- Navigate to a screen or menu
- Select / tap / press / swipe / scroll
- Enter / edit / clear / replace data
- Select / change a value
- Submit / confirm / cancel / close
- Perform authentication
- Return / go back
- Continue through the user journey
- Explicit journey position when required to establish the next action

### Forbidden Step Content

Do not write these as the primary content of Step:
- "Pastikan ..."
- "Verify ..."
- "Check ..."
- "Amati ..."
- "Sistem menampilkan ..."
- "Sistem berhasil ..."
- "Sistem gagal ..."
- "Tombol aktif ..."
- "Tombol disable ..."
- "Muncul error ..."
- "Data sesuai ..."
- "Data tersimpan ..."
- "Status berubah ..."
- "Response ..."
- API validation
- Locator validation
- Technical implementation verification

These belong in Expected unless the verification itself is explicitly
the user/tester action required by the scenario.

### Step Transformation Rule

Convert:

"Pastikan tombol Lanjut disable"

into an action-oriented flow:

"1. Pengguna berada di halaman Syarat & Ketentuan
 2. Pengguna menekan tombol Lanjut"

and put the button behavior in Expected.

Convert:

"Pastikan error Nama tabungan wajib diisi muncul"

into:

"1. Pengguna berada di halaman Tentukan Target dan Periode
 2. Pengguna membiarkan field Nama Tabungan kosong
 3. Pengguna menekan tombol Lanjut"

Expected contains the validation message and blocked navigation.

Convert:

"Pastikan data konfirmasi benar"

into:

"1. Pengguna berada di halaman Konfirmasi
 2. Pengguna meninjau informasi konfirmasi"

Expected contains the expected displayed data.

### Step Atomicity

Each numbered Step should contain one meaningful user action or
journey transition.

Do not split a natural form interaction into unnecessary micro-steps.

Example:

Good:
1. Pengguna mengisi seluruh field wajib dengan data valid
2. Pengguna menekan tombol Lanjut

Avoid:
1. Pengguna mengisi Nama Tabungan
2. Pengguna mengisi Nominal Target
3. Pengguna memilih Jangka Waktu
4. Pengguna mengisi Setoran Awal
5. Pengguna menekan tombol Lanjut

unless the individual field interaction is itself the behavior under test.

### Step Completeness

A Step sequence must contain enough navigation and user actions for
another tester to execute the scenario without guessing.

Do not omit required navigation merely because the screen is mentioned
in Pre-condition, unless that screen is explicitly the applicable entry
point for the test case.

#### Step Example — Simple Flow

```text
Step :
1. Buka Aplikasi
2. Pengguna berada di halaman Beranda
3. Pengguna memilih menu yang dituju
4. Pengguna memilih submenu yang tersedia
```

#### Step Example — End-to-End Flow

```text
Step :
1. Buka Aplikasi
2. Pengguna berada di halaman Beranda
3. Pengguna memilih menu yang dituju
4. Pengguna memilih opsi yang tersedia
5. Pengguna menekan tombol mulai
6. Pengguna menyetujui syarat dan ketentuan
7. Pengguna menekan tombol Lanjut
8. Pengguna memilih salah satu pilihan yang tersedia
9. Pengguna mengisi form sesuai data pengujian
10. Pengguna memilih periode atau opsi yang diperlukan
11. Pengguna mengisi data tambahan yang bersifat opsional jika diperlukan oleh skenario
12. Pengguna menekan tombol Lanjut
13. Pengguna memilih data yang diperlukan pada halaman berikutnya
14. Pengguna melakukan konfirmasi
15. Pengguna melakukan aksi untuk melanjutkan transaksi
16. Pengguna memasukkan kredensial atau autentikasi yang valid
```

#### Avoid

```text
Step :
1. Buka Aplikasi
2. Pastikan halaman tampil dengan benar
3. Pastikan tombol aktif
4. Pastikan data sudah benar
5. Sistem menampilkan pesan sukses
```

The items `Pastikan ...` and system responses above belong primarily in **Expected**, while **Step** should describe the tester/user actions and journey.

The Step should also remain scoped to the scenario. A validation case does not need to repeat the entire end-to-end journey if the applicable entry point can be established in Pre-condition; include only the navigation/actions needed to reach and execute the scenario.

## 13. Expected Result Language

Expected results must be written consistently in Bahasa Indonesia unless the user explicitly requests another language.

Product names, UI labels, technical terms, API names, and source-defined terminology may remain in their original form when needed for accuracy.

## 14. Final Quality Gate

A test set is not complete until a second coverage review confirms that no relevant UI element, navigation path, state transition, or meaningful flow is missing.

## Output / Template Alignment

When a test case template is provided, preserve its exact structure.

### Mobile
Use:
`TC No | Case | Menu / Module | Scenario | Pre-condition | Step | Gherkin | Expected | Actual | Assign Android | Assign iOS | Status Android | Status iOS | Evidence Android | Evidence iOS | Link Jira | Notes`

### Web
Use:
`TC No | Case | Menu / Module | Scenario | Pre-condition | Step | Gherkin | Expected | Actual | Link Jira | Notes`

Do not add or remove columns unless explicitly requested.

For newly generated cases:
- `Actual` remains blank.
- Android/iOS assignment, status, and evidence fields remain blank until execution.
- `Link Jira` remains blank unless a Jira link is supplied.
- `Notes` remains blank unless a note is required.


## Boundary & Negative Testing

# Skill: Boundary / Negative Testing

Use this skill when a feature has meaningful validation or limits.

## Negative coverage

Consider:
- Empty
- Whitespace
- Invalid format
- Invalid characters
- Malformed values
- Unexpected combinations
- Repeated actions
- Dependency failures

## Boundary coverage

When a limit is known, consider:
- min - 1
- min
- min + 1
- max - 1
- max
- max + 1

When a limit is unknown, do not invent a number. Express the behavior relative to the configured/approved limit.


## Security Testing

# Skill: Security Testing

Apply security checks according to feature risk and authorized scope.

## Common areas

- Injection
- XSS / HTML injection
- Authentication
- Authorization
- Session handling
- Sensitive data exposure
- Parameter tampering
- Replay / duplicate requests
- Rate limiting / abuse
- File upload security
- Transport security

Use safe, non-destructive checks in authorized environments.

Do not add security cases merely to increase test count; include the risks relevant to the feature.


## File Upload Testing

# Skill: File Upload Testing

For file-upload features, test beyond filename extension.

Consider:
- Supported file type
- Wrong MIME type
- Actual content mismatch
- File size boundary
- Zero-byte file
- Corrupted file
- Double extension
- Script / executable content
- Path traversal filename
- Filename encoding / special characters
- Duplicate replacement / removal
- Upload failure / retry

Validate server-side controls where the system exposes server behavior.


---

# SOURCE: AI_GENERATOR.md

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


---

# SOURCE: AUTOMATION.md

# Automation Engineering


## Context

# Context: Automation Architecture

## Established architecture

The preferred automation architecture is layered and feature-oriented:

`Feature → Step Definition → Usecase → Screen → Automation Engine → Device`

## Layer responsibilities

### Feature
Business-readable Gherkin scenarios.

### Step Definition
Thin mapping from Gherkin to Usecase methods.

### Usecase
Business flow and orchestration. Avoid screen-specific locator knowledge.

### Screen
Screen-specific UI interaction and locator knowledge.

### Shared Automation Library
Reusable technical capabilities such as UIAction, UIAssert, Wait, Swipe, Logger, and Utilities.

## Design principles

- Separation of concern
- Single responsibility
- Reusability
- Maintainability
- Scalability
- Minimal duplication
- One-way dependency flow

Prefer solving changes at the correct layer instead of modifying shared core behavior for a feature-specific need.


## Architecture Skill

# Skill: Automation Architecture

Design automation using clear layer boundaries and reusable components.

## Layer

`Feature → Step Definition → Usecase → Screen → Automation Engine → Device`

## Responsibilities

- Feature: business-readable behavior.
- Step Definition: thin BDD mapping.
- Usecase: business flow / orchestration.
- Screen: UI behavior and locators.

## Rules of design

- Keep dependencies one-way.
- Keep business logic out of generic framework utilities.
- Keep locators out of Usecase.
- Avoid duplicated technical logic across Screens.
- Prefer configuration over hardcoded environment values.
- Solve change at the narrowest responsible layer.
- Keep reusable functionality generic enough to be safely shared.


## Automation Rules

# Rules: Automation

- Keep Feature, Step Definition, Usecase, Screen, and shared framework responsibilities separate.
- Keep business flow out of shared generic utilities.
- Keep locator knowledge in Screen-level code.
- Prefer reusable helpers over duplicate implementation.
- Use stable locators.
- Keep environment-specific values configurable.
- Do not change shared core behavior for a feature-specific problem unless the behavior is truly generic.


## Change / Troubleshooting Quality Gate

Before changing shared framework code:
1. Confirm the issue is reproducible.
2. Verify the device/application/environment state.
3. Verify the Screen-level implementation and locator.
4. Verify synchronization and gesture/input handling.
5. Determine the narrowest responsible layer.

---

# SOURCE: MOBILE_AUTOMATION.md

# Mobile Automation


## Context

# Context: Mobile Automation

## Platforms

Primary mobile targets:
- Android
- iOS

Common stack:
- Katalon Studio
- Appium
- UiAutomator2 for Android
- XCUITest for iOS
- Groovy
- Real devices and simulators/emulators

## Mobile-specific behavior

Consider:
- Tap, long press, swipe, and scroll behavior
- Keyboard and custom keyboard behavior
- Native dialogs and permission prompts
- App background / foreground transitions
- Orientation changes
- Network changes
- Device-specific rendering and behavior
- Accessibility labels / resource identifiers
- Element visibility after scrolling

## Locator preference

Prefer stable identifiers exposed by the application:
- Android: `resource-id` where available
- iOS: `accessibility-id` where available

Avoid absolute XPath and fragile hierarchy-based locators.

## Automation architecture context

The established layered flow is:

`Feature → Step Definition → Usecase → Screen → Katalon/Appium → Device → Report`

Changes should be solved at the narrowest responsible layer.


## Mobile Katalon/Appium Skill

# Skill: Mobile Katalon / Appium

Use this skill for Android or iOS UI automation troubleshooting and implementation.

## Android

Prefer UiAutomator2 and stable identifiers such as `resource-id`.

For gesture behavior, use the most appropriate Appium mobile gesture command when supported by the environment. Keep gesture area and direction explicit.

For wireless debugging, verify existing pairing/connection before pairing again.

## iOS

Prefer XCUITest and stable `accessibility-id` values.

## Synchronization

Prefer condition-based waits such as element visibility / existence over fixed sleeps.

## Troubleshooting order

1. Verify device connection.
2. Verify Appium server / driver.
3. Verify app state.
4. Verify locator stability.
5. Verify synchronization.
6. Verify gesture / input behavior.
7. Only then change framework-level code.

Avoid platform-specific workarounds in shared core code unless the behavior is genuinely generic.


## Mobile Katalon Rules

# Rules: Mobile / Katalon

- Prefer Android `resource-id` and iOS `accessibility-id` when stable.
- Avoid absolute XPath and fragile hierarchy selectors.
- Use condition-based waits instead of fixed sleeps where possible.
- Keep scroll / swipe behavior scoped to the intended screen region.
- Verify device connectivity before debugging automation logic.
- Avoid repeated ADB pairing when an existing connection is valid.
- Keep platform-specific workarounds out of generic code unless they are genuinely reusable.


## Mobile Automation Quality Gate

Before finalizing a mobile automation change:
- Verify the target platform and driver.
- Verify device/app readiness.
- Prefer stable platform-native identifiers.
- Prefer condition-based synchronization.
- Keep platform-specific behavior scoped to the platform/screen that needs it.


---

# SOURCE: FIGMA_WBS.md

# Figma / SVG to WBS

## Context

# Context: Figma / SVG to WBS

Generate WBS items from Figma/SVG or equivalent UI sources specifically for QA Automation planning.

The design/source is evidence for:
- Features
- Screens
- Meaningful UI states
- Navigation
- User actions
- Forms
- Validation/error states when evidenced
- End-to-end flow relationships

Do not use an existing WBS as the source of truth unless the user explicitly asks for conformance to that WBS.

## Skill

# Skill: Figma / SVG to WBS

## Purpose

Generate a source-traceable QA Automation WBS from product requirements and UI/design sources such as Figma, SVG, screenshots, or equivalent artifacts.

## Required Hierarchy

Use:

`Squad → Big Feature → Epic / Feature → Story / Task → Sub_task`

### Big Feature
A larger product or business grouping explicitly supported by the source.

### Epic / Feature
The functional feature being automated under the Big Feature.

### Story / Task

When applicable, use:
- `Development <Feature>`
- `Integration <Feature>`
- `Locator <Feature>`

### Development / Screen

Decompose development work at screen level.

Use:
`Automation Screen <Screen Name>`

A screen-level item may represent a meaningful screen variant when the source clearly treats that variant as distinct automation work.

Do not create one ticket per button, text field, or minor UI element.

### Integration / Gherkin

Decompose meaningful end-to-end business flows.

Use:
`Gherkin Integration <Flow Name>`

Integration items should represent a complete meaningful flow, not an isolated screen.

### Locator / Object ID

Decompose automation-relevant locator work.

Use:
`Object ID <Screen / Component Name>`

Group locators at a useful automation boundary. Do not create one WBS ticket per individual locator unless the source/project explicitly requires that granularity.

## Source Analysis

Before generating:
1. Identify the Big Feature and Epic / Feature from the source.
2. Inventory screens and meaningful variants.
3. Identify navigation and user actions.
4. Identify meaningful states and validation/error states when evidenced.
5. Identify complete E2E relationships.
6. Map each source element to the appropriate WBS level.

## Rules

### Source of Truth
- Use current PRD, user story, Figma/SVG, screenshots, or equivalent source evidence.
- Do not copy an existing WBS as content unless explicitly requested.
- Preserve source terminology where practical.
- Do not invent functionality, screens, flows, or metadata.

### Metadata
Keep these blank when not explicitly supported:
- Squad
- Assignee
- Status
- Start Date
- End Date

Do not infer `Squad` from an existing example.

### Variants
Create separate screen/flow items only when the source provides evidence that they represent meaningful distinct automation work. Otherwise group them at the appropriate level.

### Traceability
Every Sub_task should be traceable to a source screen, component grouping, or meaningful E2E flow.

### Quality Gate
Before delivery verify:
- Required hierarchy is present.
- Every relevant source screen is accounted for.
- Meaningful variants are not silently omitted.
- Integration items represent real E2E flows.
- Locator work is separated from screen implementation.
- No unsupported business behavior or metadata was invented.
- The WBS schema matches the required template exactly.

## WBS Rules

# Rules: WBS

- Preserve the exact requested column order.
- Use the 9-column QA Automation schema when using the current QA Pack template:
  `Squad | Big Feature | Epic / Feature | Story / Task | Sub_task | Assignee | Status | Start Date | End Date`
- Keep `Squad` blank unless provided.
- Keep metadata blank unless provided.
- Keep Development, Integration, and Locator work distinct.
- Use screen-level Development items.
- Use meaningful E2E Integration items.
- Use automation-relevant Locator items.
- Do not make one ticket per button/field by default.
- Do not copy example WBS content into a new source-derived WBS.
- Preserve source-derived ordering where it improves traceability.


---

# SOURCE: TEMPLATES.md

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


---

# SOURCE: NAMING_AND_OUTPUT.md

# Naming & Output Rules


## Naming Rules

# Rules: Naming

Use clear, consistent, descriptive names.

Established automation naming:
- Groovy Screen: `PascalCase<Screen>.groovy`
- Python / Playwright Screen: `kebab-case-<screen>-screen.py`

Do not encode product-specific names into generic rules unless explicitly required by the current project.


## File Output Rules

# Rules: File Output

- Preserve the requested output format.
- Keep generated files directly usable by the target tool.
- Use timestamped output names when the workflow requires versioned artifacts.
- Validate that the output file exists and is readable before delivery.
- Never present a file as complete if key content failed to generate.


## QA Artifact Naming

Use clear, descriptive, task-oriented names.

Recommended generated artifact names:
- Test Case: `TC_<Feature>_<Platform>.xlsx`
- QA Automation WBS: `WBS_<Feature>_QA_Automation.xlsx`

Do not add dates or versions unless versioning is explicitly required by the workflow.

## Output Validation

Before delivery:
- Confirm the file exists.
- Confirm the file is readable/openable.
- Confirm the schema matches the requested template.
- Confirm execution-only fields are blank when the artifact is unexecuted.
- Confirm no required source-derived content was omitted.


---

# SOURCE: DOCUMENTATION.md

# Documentation & Handover


## Context

# Context: Documentation

Technical handover documentation should be client-friendly, practical, and easy to maintain.

Typical framework handover topics:
- Purpose & Scope
- Architecture Principles
- High-Level Architecture & Pattern
- Tech Stack & Dependencies
- API / DB Integration
- Security / Data Protection
- CI/CD

Use diagrams where they improve understanding, especially architecture, technology stack, folder structure, and execution flow.


## Skill

# Skill: Documentation / Handover

Create practical technical documentation that can be used by the receiving team without relying on verbal explanation.

## Typical structure

1. Purpose & Scope
2. Architecture Principles
3. High-Level Architecture & Pattern
4. Tech Stack & Dependencies
5. API / DB Integration
6. Security / Data Protection
7. CI/CD
8. Maintenance / Operational Notes when relevant

Use diagrams for architecture, technology stack, folder structure, and execution flow when they add value.

Keep wording client-friendly and avoid unnecessary formality.


## Rules

# Rules: Documentation

- Preserve factual accuracy.
- Do not invent architecture, tools, dependencies, or requirements.
- Keep wording practical and easy to follow.
- Use diagrams when they materially improve understanding.
- Respect requested page limits and document templates.
- Formatting-only requests must not change content meaning.


## Knowledge Base Maintenance

When documenting the QA Pack itself:
- Keep context, skills, rules, and templates conceptually separated.
- Avoid duplicating the same rule across multiple files unless the duplication is necessary for routing clarity.
- Update dependent documentation when a canonical template or rule changes.


---

# SOURCE: README.md

# QA Engineering ChatGPT Pack

This pack is the reusable QA Engineering Knowledge Base optimized for ChatGPT Projects.

## Structure

The pack separates responsibilities conceptually:

- `MASTER_INSTRUCTIONS.md` — routing, precedence, and global rules
- `QA_TEST_CASE_GENERATION.md` — test case generation skill + rules
- `AUTOMATION.md` — automation architecture skill/context/rules
- `MOBILE_AUTOMATION.md` — mobile Katalon/Appium context/skill/rules
- `JENKINS_CI_CD.md` — CI/CD context/skill/rules
- `REPORTING.md` — reporting and log analysis
- `DOCUMENTATION.md` — documentation and handover
- `AI_GENERATOR.md` — source-to-artifact AI workflow
- `FIGMA_WBS.md` — Figma/SVG to QA Automation WBS
- `TEMPLATES.md` — canonical test case and WBS output schemas
- `NAMING_AND_OUTPUT.md` — naming and file-output rules

## Recommended upload order

1. `MASTER_INSTRUCTIONS.md`
2. `QA_TEST_CASE_GENERATION.md`
3. `TEMPLATES.md`
4. `FIGMA_WBS.md`
5. `AUTOMATION.md`
6. `MOBILE_AUTOMATION.md`
7. `JENKINS_CI_CD.md`
8. `REPORTING.md`
9. `DOCUMENTATION.md`
10. `AI_GENERATOR.md`
11. `NAMING_AND_OUTPUT.md`

## Usage

Use the smallest relevant set for each task. Do not assume every document applies to every task.

The current source/requirement/design remains the primary source of truth. This pack provides reusable QA engineering behavior and constraints.

## Current QA Test Case Conventions

- Case: `Positive` / `Negative`
- Expected: Bahasa Indonesia unless explicitly requested otherwise
- Pre-condition: state/setup already true before execution
- Step: tester actions from the applicable entry point through the target outcome
- No invented requirements, limits, metadata, execution results, or evidence

## Current QA Automation WBS Conventions

Hierarchy:

`Squad → Big Feature → Epic / Feature → Story / Task → Sub_task`

Schema:

`Squad | Big Feature | Epic / Feature | Story / Task | Sub_task | Assignee | Status | Start Date | End Date`

`Squad`, `Assignee`, `Status`, `Start Date`, and `End Date` remain blank unless the source explicitly provides them.

## Maintenance

When a project-level rule changes, update the affected canonical file(s) and then synchronize dependent files such as `MASTER_INSTRUCTIONS.md`, `TEMPLATES.md`, and `README.md`.

Avoid accumulating duplicate or obsolete rules.


---

# SOURCE: UPDATE_MANIFEST.md

# QA Pack Update Manifest

Updated: 2026-09-17

## Main synchronization changes

- Removed the deprecated `Regression UAT` test-case field/rule.
- Standardized Case to `Positive` / `Negative`.
- Standardized Expected Result language to Bahasa Indonesia unless explicitly requested otherwise.
- Clarified Pre-condition vs Step responsibilities.
- Canonicalized current Mobile and Web test-case templates.
- Canonicalized QA Automation WBS hierarchy:
  `Squad → Big Feature → Epic / Feature → Story / Task → Sub_task`
- Canonicalized current 9-column WBS schema:
  `Squad | Big Feature | Epic / Feature | Story / Task | Sub_task | Assignee | Status | Start Date | End Date`
- Explicitly prohibited inferred Squad/Assignee/Status/Date metadata.
- Clarified that new WBS must be source-derived and must not silently copy an existing WBS.
- Synchronized README, MASTER_INSTRUCTIONS, TEMPLATES, FIGMA_WBS, and AI_GENERATOR routing.
- Preserved the existing automation architecture and mobile/Jenkins/reporting/documentation guidance, while adding aligned quality gates.

