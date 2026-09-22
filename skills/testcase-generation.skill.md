# Test Case Generation Skill

Input:
- APPROVED analysis.md
- applicable QA rules
- testcase schema
- testcase template

Process:
1. Read the complete approved analysis.
2. Inventory screens, elements, states, flows, validations, dependencies, and unknowns.
3. Generate positive and negative cases supported by the analysis.
4. Apply boundary coverage only where supported.
5. Ensure Pre-condition / Step / Expected separation.
6. Align Gherkin with the case.
7. Perform a second coverage review.
8. Validate output against testcase schema.

Output:
- testcase.json

Do not generate unsupported requirements or execution results.
