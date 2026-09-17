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
