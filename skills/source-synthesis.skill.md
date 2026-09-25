# Source Synthesis Skill

## Purpose

Combine multiple source analyses into one QA-ready source-of-truth for downstream test case generation.
The synthesis must reconcile information from multiple source analyses without inventing requirements, UI behavior, business rules, or technical implementation details.
The skill must produce two output artifacts:

1. Result Analysis
2. Feedback

The Result Analysis describes what is supported, confirmed, unresolved,
conflicting, and unknown based on the provided sources.

The Feedback describes what is still missing or unresolved when the
synthesized result is not ready for test case generation.

The synthesis must not invent requirements, UI behavior, business rules,
validation, calculations, or technical implementation details.

---

## Inputs

The skill may receive one or more source analyses, such as:

- Figma / UI analysis
- User Story analysis
- PRD analysis
- Existing application behavior analysis
- Other explicitly provided requirement analysis

Each input must retain its source identity and provenance.

---

## Source Precedence

When sources provide different information:

1. Current task-specific source
2. Current approved requirement / product source
3. Current UI / design evidence
4. Older or general project knowledge

Do not silently resolve contradictions.

If two sources conflict:

- preserve both pieces of evidence
- identify the conflict
- mark the affected requirement as unresolved
- do not choose one without supporting evidence

---

## Synthesis Rules

### 1. Preserve Provenance

Every synthesized requirement or behavior must be traceable to one or more source analyses.

Preserve source terminology where applicable.

Do not remove important context required for downstream QA analysis.

### 2. Separate Evidence From Interpretation

Classify information as:

- Confirmed
- Partially Confirmed
- Inferred
- Unknown
- Conflicting

Do not present an inference as a confirmed requirement.

### 3. Do Not Invent

Never invent:

- screens
- UI elements
- labels
- buttons
- navigation
- validation rules
- minimum / maximum values
- business rules
- calculations
- error messages
- error handling
- API behavior
- database behavior
- authentication behavior
- security behavior
- execution results

If information is missing, record it as Unknown or Requirement Gap.

---

# QA Coverage Synthesis

The synthesis must consolidate evidence for the following areas.

## User Journey

Identify:

- entry points
- main flow
- alternate flows
- branch flows
- completion / success flow

Only include flows supported by source evidence.

---

## Screen / UI

Identify:

- screens
- sections
- visible elements
- interactive controls
- input fields
- read-only fields
- calculated fields
- CTA
- navigation controls

Do not infer UI components solely from common design patterns.

---

## Interaction

Identify supported interactions such as:

- selection
- input
- submission
- confirmation
- edit
- navigation
- back
- cancel
- retry
- exit

Only record interactions when supported by evidence.

---

# States

Identify supported UI and functional states such as:

- default
- selected
- unselected
- enabled
- disabled
- loading
- error
- warning
- empty
- success
- read-only
- expanded
- collapsed

If a state is not evidenced:

- do not assume it exists
- mark it as Not Specified or Unknown when relevant

Absence of evidence must not be interpreted as proof that the state does not exist.

---

# Business Rule Synthesis

Identify and consolidate:

- product / feature variants
- eligibility
- required / optional fields
- field dependencies
- calculations
- limits
- date rules
- amount rules
- account rules
- transaction rules
- confirmation requirements

For each rule, identify:

- rule
- evidence
- status
- unresolved ambiguity

Exact values, formulas, or limits must only be included when supported by source evidence.

---

# Variant Analysis

Explicit variants must be compared rather than merely listed.

For each variant, identify whether differences are known in:

- screen
- field
- UI
- validation
- calculation
- business rule
- navigation
- confirmation
- success result

Example:

Variant A vs Variant B

Status:
Confirmed variants

Known differences:
Unknown

QA impact:
Clarification required

Do not infer differences merely because variants have different names or labels.

---

# Validation / Error Synthesis

Consolidate all source-supported:

- validation rules
- negative conditions
- error states
- blocking behavior
- recovery behavior
- retry behavior
- timeout behavior

Separate:

### Explicit Negative Conditions

Conditions explicitly stated by the source.

### Potential QA Gaps

Conditions that may be relevant to QA but are not specified by the source.

Potential QA gaps must not automatically become test cases.

---

# Navigation Synthesis

Build the supported navigation relationship between screens.

Capture:

- source screen
- action
- destination
- prerequisite
- branch
- alternate path

Back, cancel, edit, retry, and exit behavior must only be recorded when supported by evidence.

---

# Data / Calculation Dependencies

Identify relationships between inputs and outputs.

For example:

Input A
    ↓
Calculated Field B

Only record the dependency when supported by source evidence.

If the source indicates that a field is calculated but does not define:

- formula
- trigger
- rounding
- dependency

mark those items as Unknown.

---

# Gap Classification

Classify unresolved information into the following categories.

## Requirement Gap

Missing business requirement or acceptance behavior.

## UI Gap

Missing UI, component, layout, or state information.

## Business Rule Gap

Missing rule, condition, limit, eligibility, or calculation.

## Validation Gap

Missing input format, range, mandatory rule, or validation behavior.

## Navigation Gap

Missing back, cancel, edit, retry, exit, or transition behavior.

## Error Handling Gap

Missing error, timeout, recovery, or service-failure behavior.

## Security Gap

Missing security-related behavior where the source indicates sensitive information, authentication, authorization, or protected actions.

## Technical Gap

Missing API, database, integration, device, environment, or other technical behavior.

Do not convert a gap into an assumed requirement.

---

# Clarification Questions

Generate focused questions for unresolved items.

Questions must be:

- specific
- actionable
- traceable to a source gap
- useful for QA coverage

Avoid generic questions such as:

> Is there anything else?

Questions should identify exactly what information is required to remove the ambiguity.

---

## Evidence-Linked Clarification Synthesis

When consolidating source analyses, preserve every material Unknown, Conflict, Ambiguity, Requirement Gap, or unsupported assumption that can affect QA coverage.

For each material clarification item:

1. Preserve the clarification question from the source analysis.
2. Preserve the supporting source evidence/reference.
3. Preserve conflicting evidence when multiple sources disagree.
4. Preserve the QA impact of the unresolved item.
5. Preserve the resolution status:
   - Unknown
   - Conflicting
   - Ambiguous
   - Clarification Required
   - Resolved
6. Do not resolve conflicts during synthesis unless the higher-precedence source explicitly resolves them.
7. Do not convert inferred or partially confirmed behavior into confirmed requirements.
8. Do not remove a clarification merely because another source does not mention the issue.
9. If multiple source analyses identify the same gap, consolidate them into one clarification item while preserving all relevant source references.
10. If two clarification items appear similar but have different QA impacts or different source evidence, keep them separate.

### Recommended Clarification Output

Use:

| # | Clarification Question | Source Evidence | Conflict / Gap | QA Impact | Status |
|---|---|---|---|---|---|
| 1 | <question> | <source/page/section/line> | <conflict or missing evidence> | <impact to QA coverage> | <status> |

### Clarification Priority

When useful, classify unresolved items:

#### P0 — Blocking for Test Case Generation

Use when unresolved clarification can materially change:
- user journey / testcase flow;
- expected result;
- validation;
- boundary;
- calculation;
- state transition;
- eligibility;
- required testcase coverage.

#### P1 — Important for Coverage

Use when unresolved clarification affects meaningful QA coverage but does not necessarily block the complete testcase scope.

### Synthesis Decision

The synthesis must explicitly state whether each material clarification:

- remains unresolved;
- has been resolved by a higher-precedence source;
- remains conflicting across sources; or
- is no longer relevant to the intended QA scope.

Unresolved items must remain gaps and must not be converted into concrete testcase conditions.

### Traceability Requirement

Every material clarification in the synthesis must be traceable back to one or more source-analysis inputs.

Do not invent source references, answers, priorities, or resolution status.

---

# QA Readiness

QA Readiness is a generation gate that determines whether it is safe
to proceed to test case generation without introducing unsupported assumptions.

The status must be one of:

## READY

Use only when the available source evidence is sufficient for the intended
test case scope and test case generation can proceed without inventing
requirements, UI behavior, business rules, validation, or technical behavior.

## NOT READY

Use when unresolved information could require assumptions during test case
generation.

NOT READY includes cases where the analysis is partially complete but
critical information remains unresolved.

Do not use a separate PARTIALLY_READY status.

## Readiness Details

When QA Readiness is NOT READY, summarize the readiness of each relevant area:

| Area | Status | Impact |
|---|---|---|
| Main Journey | Sufficient / Insufficient | ... |
| UI Evidence | Sufficient / Partial / Insufficient | ... |
| Business Rules | Sufficient / Partial / Insufficient | ... |
| Variants | Sufficient / Partial / Insufficient | ... |
| Validation | Sufficient / Partial / Insufficient | ... |
| Navigation | Sufficient / Partial / Insufficient | ... |
| Error Handling | Sufficient / Partial / Insufficient | ... |
| Security | Sufficient / Partial / Insufficient / N/A | ... |
| Technical | Sufficient / Partial / Insufficient / N/A | ... |

---

## Test Case Generation Gate

Test case generation may proceed only when:

QA Readiness = READY

If:

QA Readiness = NOT READY

then:

1. identify unresolved gaps
2. generate clarification questions
3. update the source requirements / analysis
4. rerun source synthesis
5. reevaluate QA Readiness

Do not generate test cases while QA Readiness is NOT READY.

---

# Output Structure

The synthesized analysis should contain:

1. Metadata
2. Source Inputs
3. Confirmed User Journey
4. Screen / Section Inventory
5. UI / Component Inventory
6. Functional Requirements
7. Business Rules
8. Variants
9. UI States
10. Navigation
11. Validation / Error / Success
12. Data / Calculation Dependencies
13. Dependencies / Constraints
14. Requirement Gaps
15. UI Gaps
16. Business Rule Gaps
17. Validation Gaps
18. Navigation Gaps
19. Error Handling Gaps
20. Security Gaps
21. Technical Unknowns
22. Clarification Questions
23. Traceability
24. QA Readiness

---

# Quality Gate

Before producing the synthesis, verify:

- all provided source analyses were considered
- source terminology is preserved
- provenance is maintained
- conflicting evidence is surfaced
- unknowns are explicitly marked
- unsupported requirements were not introduced
- UI behavior was not invented
- variants are compared where applicable
- negative conditions are distinguished from potential QA gaps
- calculation dependencies are not assumed
- navigation behavior is evidence-based
- gaps are classified correctly
- clarification questions are actionable
- QA readiness is explicitly stated

The synthesis must remain a source-of-truth analysis and must not generate test cases.