# QA Manual WBS Generation Skill

## Purpose

Generate a structured Work Breakdown Structure (WBS) for QA Manual activities based on an approved source analysis or source synthesis.

The WBS translates product requirements and user journeys into manageable QA testing activities.

The WBS is a planning artifact.

It is not:
- a test case
- a test scenario list
- an execution result
- a defect list
- a project schedule unless scheduling information is explicitly provided

---

## Input

Primary input:

- Approved Source Synthesis
- Approved User Story / PRD Analysis
- Approved Figma / UI Analysis when applicable

Supporting input may include:

- Existing QA requirements
- Application behavior
- Test scope
- Explicit user instructions

The current approved source must remain the primary source of truth.

---

## Core Process

Use the following workflow:

Source
→ Understand Scope
→ Identify User Journey
→ Identify QA Work Areas
→ Decompose Testing Activities
→ Build WBS
→ Validate Coverage
→ Output

---

## 1. Understand Feature Scope

Identify:

- feature scope
- in-scope functionality
- out-of-scope functionality
- primary user journey
- alternate flows
- negative flows
- transaction/result states
- post-transaction activities
- dependencies
- known constraints
- known gaps

Do not create WBS activities for unsupported functionality.

---

## 2. Identify QA Work Areas

Translate the source into meaningful QA work areas.

Common QA work areas include:

- Test Preparation
- Functional Testing
- Negative & Exception Testing
- UI / UX Testing
- Integration / Data Validation
- Regression Testing

Only include categories that are relevant to the feature.

Additional categories may be created when the source clearly requires them.

---

## 3. Decompose Functional Testing

Break functional testing according to meaningful business capabilities or user journey stages.

Examples:

- Transfer Entry & Navigation
- Bank Selection
- Destination Account
- Transfer Input
- Transfer Purpose
- Transfer Confirmation
- PIN Verification
- Transaction Result
- Post Transaction

The decomposition should follow the actual feature behavior.

Do not create one WBS item for every individual UI field or button.

---

## 4. Decompose Negative & Exception Testing

Identify source-supported negative and exception conditions.

Examples:

- invalid input
- missing mandatory input
- invalid account
- insufficient balance
- transaction limit
- invalid PIN
- blocked account
- system error
- network failure
- timeout
- failed transaction

Group related conditions into meaningful QA activities.

---

## 5. Decompose UI / UX Testing

Include UI / UX validation when the source contains meaningful visual or interaction requirements.

Examples:

- screen layout
- component visibility
- labels
- enabled / disabled state
- selected / unselected state
- validation messages
- loading state
- success / failure state
- formatting
- truncation
- masking

Do not turn every UI element into a separate WBS task.

---

## 6. Decompose Integration / Data Validation

Include integration or data validation activities when the source provides data dependencies or cross-system behavior.

Examples:

- inquiry result
- account information
- balance
- transaction limit
- transaction status
- transaction reference
- calculated transaction amount
- consistency between confirmation and result

Do not invent API, database, or technical validation activities when they are not supported by the source.

---

## 7. Decompose Regression Testing

Regression activities should cover meaningful existing functionality that could be impacted by the feature.

Examples:

- main flow regression
- validation regression
- transaction result regression
- authentication / PIN regression
- post-transaction regression

Do not automatically create regression activities for unrelated functionality.

---

## 8. WBS Granularity

WBS should be:

- meaningful
- actionable
- testable as a work activity
- easy to estimate
- easy to track
- traceable to source requirements

Avoid:

### Too broad

`Test Transfer Feature`

### Too granular

`Verify Nominal Label`

`Verify Nominal Field`

`Verify Nominal Icon`

`Verify Nominal Placeholder`

Instead use:

`Transfer Input`

with relevant sub-tasks covering the meaningful behaviors.

---

## 9. WBS vs Test Case

WBS defines:

> What QA work needs to be performed?

Test cases define:

> How will each behavior be tested?

Example:

WBS:

`Transfer Input`
→ `Verify transfer amount validation`

Test cases may later contain:

- empty amount
- zero amount
- valid amount
- amount exceeding limit
- formatting behavior

Do not prematurely convert every potential test case into a WBS item.

---

## 10. Coverage Review

Before finalizing the WBS, verify coverage against:

### User Journey

Entry
→ Input
→ Selection
→ Confirmation
→ Verification
→ Processing
→ Result
→ Post Transaction

### QA Coverage

Functional
→ Validation
→ Negative / Exception
→ UI / UX
→ Integration / Data
→ Regression

### Source Evidence

Requirements
→ Business Rules
→ States
→ Navigation
→ Dependencies
→ Known gaps

Identify missing meaningful QA activities before delivery.

---

## 11. Output

Generate a structured WBS.

Recommended structure:

Feature
→ Category
→ Task
→ Sub-task

Example:

Transfer On Us
→ Functional Testing
→ Transfer Input
→ Verify transfer amount input

Optional metadata may include:

- WBS ID
- Assignee
- Status
- Start Date
- End Date

Metadata must only be populated when provided by the source or user.

---

## 12. Traceability

Every WBS task should be traceable to one or more:

- requirements
- business rules
- user journey steps
- UI behavior
- validation rules
- transaction states
- dependencies

If a WBS item cannot be traced to the source, review whether it is an unsupported assumption.

---

## Output Quality

A good QA Manual WBS should:

- represent the complete meaningful testing scope
- follow the actual user journey
- separate testing concerns logically
- avoid unnecessary micro-tasks
- identify negative and exception work
- include relevant UI / UX work
- include relevant data / integration validation
- include regression where relevant
- remain independent from test-case-level detail
- remain traceable to the source
