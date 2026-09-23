# QA Manual WBS Generation Rules

## 1. Source of Truth

Generate the WBS from the current approved source.

Source precedence:

1. Explicit current user instruction
2. Current approved Source Synthesis
3. Current approved User Story / PRD Analysis
4. Current approved Figma / UI Analysis
5. Other explicitly supplied QA context
6. Generic QA knowledge

Do not use generic assumptions to override source evidence.

---

## 2. No Unsupported Requirements

Do not invent:

- requirements
- business rules
- screens
- user flows
- validation rules
- limits
- calculations
- error behavior
- technical behavior
- API behavior
- database behavior
- security behavior
- test results
- execution status

If information is unknown, do not convert it into a WBS requirement.

---

## 3. WBS Purpose

The WBS must represent QA work planning.

Do not generate a WBS as:

- test cases
- Gherkin scenarios
- step-by-step execution instructions
- defect reports
- automation implementation tasks

unless explicitly requested.

---

## 4. QA Manual Focus

For QA Manual WBS, prioritize:

- requirement understanding
- functional validation
- user journey coverage
- input validation
- business rule validation
- negative testing
- exception handling
- UI / UX validation
- integration / data validation
- regression

Do not introduce automation-specific activities such as:

- Object ID
- Locator
- Screen automation
- Step Definition
- Usecase
- Gherkin automation
- framework implementation

unless the user explicitly requests an automation WBS.

---

## 5. Recommended Hierarchy

Use:

Feature
→ Category
→ Task
→ Sub-task

Example:

Transfer On Us
→ Functional Testing
→ Transfer Input
→ Verify transfer amount validation

The hierarchy may be adapted when the source or project requires a different structure.

---

## 6. Meaningful Decomposition

Create a separate task when it represents a meaningful QA responsibility.

Good:

- Transfer Input
- PIN Verification
- Transaction Result
- Negative & Exception Testing

Avoid:

- Verify Button
- Verify Label
- Verify Icon
- Verify Text Color

unless the individual UI element represents a distinct business or QA responsibility.

---

## 7. User Journey Coverage

The WBS should cover the meaningful end-to-end journey.

When applicable, consider:

- entry
- navigation
- input
- selection
- validation
- confirmation
- authentication / verification
- processing
- success
- failure
- processing / pending
- post-transaction action

Do not stop decomposition at the first successful screen when the business flow continues.

---

## 8. Positive and Negative Coverage

Functional WBS should include both:

### Positive

Expected successful behavior.

### Negative / Exception

Invalid, blocked, failed, unavailable, or exceptional behavior.

Do not assume every negative condition exists.

Only include source-supported negative conditions.

---

## 9. Boundary Coverage

Do not create boundary-specific WBS activities when the source does not define an exact boundary.

For example:

If the source specifies:

`Maximum note length = 40 characters`

boundary testing may be represented.

If the source only says:

`Amount has a limit`

but does not provide the actual value:

do not invent boundary values.

---

## 10. UI / UX Coverage

When UI evidence exists, consider:

- layout
- visibility
- labels
- input states
- enabled / disabled CTA
- selected state
- error state
- loading state
- success state
- failure state
- formatting
- masking
- truncation

Do not infer UI behavior that is not supported by the source.

---

## 11. Integration / Data Coverage

Create integration or data-validation WBS items only when supported by source evidence.

Examples:

- account inquiry result
- balance validation
- transaction limit
- transaction status
- transaction reference
- confirmation vs result consistency

Do not assume specific APIs, databases, endpoints, or service architecture.

---

## 12. Regression

Regression is included when:

- explicitly requested
- existing functionality is affected
- the source identifies dependencies or impacted functionality
- the QA scope requires regression

Do not create unrelated regression activities.

---

## 13. Known Gaps

Known source gaps should not automatically become test activities.

Example:

Source says:

`Account number length is unspecified.`

Do not create:

`Verify account number length`

Instead, retain the gap as a requirement clarification item if the workflow supports gap tracking.

---

## 14. Conflicting Sources

If source materials conflict:

- preserve the conflict
- do not silently choose one behavior
- do not create a WBS item based on an unsupported resolution

Example:

Source A:

`Favorite is out of scope.`

Source B:

`Favorite exists after successful transaction.`

Do not assume which behavior is final.

Create the WBS based on the confirmed scope and retain the conflict for clarification.

---

## 15. Metadata

Do not infer:

- Assignee
- Status
- Start Date
- End Date
- Story Point
- Estimate

Leave these fields empty unless explicitly provided.

---

## 16. Naming

Use concise, action-oriented names.

Preferred:

`Transfer Input`

`PIN Verification`

`Transaction Result`

`Input Validation`

Avoid vague names:

`Testing Transfer`

`Check Everything`

`Miscellaneous`

---

## 17. Avoid Duplication

Do not duplicate the same QA activity across multiple categories unless the activities represent genuinely different testing concerns.

Example:

Do not create the same:

`Verify insufficient balance`

under multiple identical tasks.

---

## 18. WBS Completeness

Before delivery, verify:

- feature scope is represented
- primary journey is represented
- meaningful alternate flows are represented
- negative conditions are represented
- result states are represented
- post-transaction behavior is represented
- UI / UX coverage is represented when applicable
- integration / data coverage is represented when applicable
- regression is represented when applicable
- known source gaps are not converted into assumptions

---

## 19. WBS Is Not Test Case Coverage

Do not attempt to represent every test case in the WBS.

A single WBS task may produce multiple test scenarios and test cases.

Example:

WBS:

`Input Validation`

may later produce:

- empty input
- invalid input
- valid input
- boundary input
- formatting input

The WBS remains at the appropriate planning level.

---

## 20. Final Quality Gate

Before delivering the WBS, verify:

- correct source of truth was used
- source terminology is preserved
- no unsupported requirements were introduced
- no technical assumptions were introduced
- QA Manual scope is represented
- user journey is covered
- positive and negative work is represented
- meaningful UI / UX work is represented
- relevant integration / data work is represented
- relevant regression work is represented
- no unnecessary micro-tasks were created
- metadata was not guessed
- known gaps remain gaps
- WBS remains distinguishable from test cases
- every meaningful WBS item is traceable to source evidence
