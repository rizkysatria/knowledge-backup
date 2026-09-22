# Test Case Generation Rules

1. Generate only from approved source analysis and applicable project rules.
2. Follow the supplied test case schema/template exactly.
3. Complete the user journey: actions, responses, state changes, navigation, alternate outcomes, recovery, and final state where supported.
4. Cover meaningful positive and negative behavior.
5. Apply boundary testing only when the source supports an exact limit.
6. Pre-condition describes what is already true before execution.
7. Step describes tester/user actions.
8. Expected describes observable system behavior.
9. Expected Result is Bahasa Indonesia unless explicitly requested otherwise.
10. Gherkin must align with Scenario, Step, and Expected.
11. Do not fabricate execution results, evidence, metadata, counts, or statuses.
12. Leave execution-only fields blank for unexecuted cases.
13. Avoid redundant micro-cases while maintaining meaningful coverage.
14. Perform a second coverage review before delivery.
