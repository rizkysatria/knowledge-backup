# Test Case Generation Skill

Input:
- APPROVED analysis.md
- applicable QA rules
- testcase schema
- testcase template

Process:
1. Read the complete approved analysis.
2. Inventory screens, elements, states, flows, validations, dependencies, and unknowns.
3. Identify the applicable journey entry point for each test scenario.
4. Generate positive and negative cases supported by the analysis.
5. Apply boundary coverage only where supported.
6. Ensure every testcase is independently executable and does not depend on another testcase.
7. Build each Step from the applicable journey entry point through all required navigation and actions until the target behavior is reached.
8. Ensure Pre-condition, Step, and Expected are clearly separated.
9. Keep Pre-condition limited to initial state, required data, account/session state, or environment setup that must already exist before execution.
10. Do not use Pre-condition to describe the screen or navigation state that should be reached by the Step.
11. Do not shortcut source-defined navigation just because another testcase already covers the same path.
12. Ensure Expected describes observable system behavior resulting from the executed Step.
13. Align Gherkin with the scenario, the complete business flow in Step, and the Expected result while maintaining reusable business actions.
14. Perform a second coverage review against:
    - user journey
    - screen/UI inventory
    - validations
    - states
    - navigation
    - alternate flows
    - negative/error flows
    - recovery flows
15. Validate output against testcase schema.

Standalone Test Case Principle:
- Each testcase must be executable independently.
- Each testcase must have its own complete execution path from the applicable journey entry point.
- Testcases must not assume that a previous testcase has been executed.
- Shared navigation may be repeated across testcases.
- Step must contain the navigation required to reach the target scenario.
- Pre-condition must not contain navigation steps.
- If a scenario starts from a specific feature entry point, every applicable testcase should start from that same entry point unless the approved analysis explicitly defines another entry point.
- For scenarios targeting a later state in the journey, Step must traverse the required earlier flow before executing the target action.
- For post-transaction scenarios, Step must include the transaction flow required to reach the relevant transaction result before performing the post-transaction action.
- If a target state cannot be reached deterministically based on the approved analysis, do not invent a setup mechanism. Preserve the gap or use only explicitly supported preconditions.

## Gherkin Reusability Principle

Gherkin is not only a readable representation of the testcase.
It should also be suitable for reuse in automation.

- Given represents the applicable feature entry point.
- When / And represents meaningful reusable business actions.
- Do not unnecessarily split one reusable business action into multiple low-level UI actions.
- When the same business flow occurs across multiple test cases, use the same Gherkin wording.
- Common flows should be represented as reusable business steps where appropriate.
- Avoid scenario-specific wording when the same reusable action can be used.
- Then represents the scenario-specific observable outcome.

Output:
- testcase.json

Do not:
- generate unsupported requirements
- generate execution results
- assume dependency on another testcase
- omit required navigation because it was already covered by another testcase
- place navigation or screen location in Pre-condition
- invent setup mechanisms for unsupported states