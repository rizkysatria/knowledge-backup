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

## 11. Risk / Regression

Use Regression UAT and priority intentionally. Do not mark every case as critical.

## 12. Final Quality Gate

A test set is not complete until a second coverage review confirms that no relevant UI element, navigation path, state transition, or meaningful flow is missing.
