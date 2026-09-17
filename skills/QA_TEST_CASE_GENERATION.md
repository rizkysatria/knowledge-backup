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
