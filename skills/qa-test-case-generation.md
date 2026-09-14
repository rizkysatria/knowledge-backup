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
