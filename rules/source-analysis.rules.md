# Source Analysis Rules

1. Current source / requirement / application behavior has precedence over generic assumptions.
2. Do not invent screens, UI elements, interactions, states, validations, business rules, limits, calculations, navigation, or implementation details.
3. Record unknowns explicitly when the source does not provide enough evidence.
4. Preserve source terminology, source wording where relevant, and traceability.
5. Inventory relevant screens, sections, visible UI, interactive UI, states, navigation evidence, alternate/error evidence, and dependencies when supported by the source.
6. Distinguish observed facts from interpretation, inference, and clarification needs.
7. If sources conflict, surface the conflict instead of silently resolving it. Preserve the relevant conflicting source evidence.
8. Produce analysis in Markdown according to the analysis template/schema.
9. For every material Unknown, Conflict, Ambiguity, or Requirement Gap that can affect QA coverage, create an explicit clarification question.
10. Every material clarification question must include:
    - the clarification question;
    - source reference/evidence;
    - the QA reason or impact.
11. Clarification questions must describe an existing gap in the source and must not introduce, assume, or define a new requirement.
12. When multiple source statements create a conflict, reference the relevant source evidence for each conflicting statement.
13. Do not resolve Unknown, Conflict, or Ambiguity using generic QA knowledge, assumptions, or inferred product behavior.
14. Clarification priority may be identified when useful:
    - P0 — Blocking for Test Case Generation
    - P1 — Important for Coverage
15. Use P0 when an unresolved item can materially change testcase flow, expected result, validation, boundary, calculation, state transition, eligibility, or required coverage.
16. Use P1 when an unresolved item affects meaningful QA coverage but does not necessarily block the complete testcase scope.
17. Unresolved clarification items remain Unknown / Conflicting / Ambiguous and must not be converted into concrete testcase conditions until the source requirement is clarified or approved.