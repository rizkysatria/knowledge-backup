# QA Engineering — Modular Master Instructions

## Purpose

This file is the entry point for the token-efficient QA knowledge pack.

Use it to route a task to the smallest relevant set of files. Do not load the legacy consolidated pack (`QA_PROJECT_KNOWLEDGE.md`) for a modular workflow unless the user explicitly asks to use or compare it.

The modular pack separates work into small, composable units:

- `skills/` — task-specific analysis or generation method
- `rules/` — mandatory constraints and quality gates
- `schemas/` — machine-readable output contract
- `templates/` — human-readable review format or output starter

The current task source (PRD, user story, Figma, SVG, screenshot, API contract, or observed behavior) remains the primary source of truth.

---

## 1. Operating Model

For every task:

`Identify task → identify source → load minimum modules → analyze → validate → output`

Load a skill only when its source type or output is relevant. Load a rule only when performing the governed activity. Do not preload every skill, rule, schema, or template.

### Source-of-truth precedence

When information conflicts, use this order:

1. Explicit current user instruction
2. Current task source or observed application behavior
3. Explicit project context supplied with the task
4. Applicable modular skill, rule, schema, or template
5. Generic QA assumptions

Never use a generic assumption to override source evidence.

### Evidence discipline

Do not invent requirements, UI behavior, business rules, validation limits, screens, navigation, states, test results, evidence, dates, status, assignees, or implementation details.

When the source does not provide enough evidence, record the item as unknown, open question, or requirement-dependent. Surface source conflicts instead of silently resolving them.

---

## 2. Task Routing

| Task | Load | Output |
| --- | --- | --- |
| Analyze a PRD | `skills/prd-analysis.skill.md`, `rules/source-analysis.rules.md`, `templates/analysis-template.md`, `schemas/analysis.schema.json` | Source analysis (`DRAFT`) |
| Analyze a user story | `skills/user-story-analysis.skill.md`, `rules/source-analysis.rules.md`, `templates/analysis-template.md`, `schemas/analysis.schema.json` | Source analysis (`DRAFT`) |
| Analyze Figma, SVG, or screenshot | `skills/figma-analysis.skill.md`, `rules/source-analysis.rules.md`, `templates/analysis-template.md`, `schemas/analysis.schema.json` | Source analysis (`DRAFT`) |
| Combine multiple analyses | `skills/source-synthesis.skill.md`, `rules/source-analysis.rules.md`, `templates/analysis-template.md`, `schemas/analysis.schema.json` | Unified source analysis (`DRAFT`) |
| Review an analysis | `templates/approval-template.md` plus original source | `DRAFT`, `CHANGES_REQUESTED`, or `APPROVED` |
| Generate test cases | `skills/testcase-generation.skill.md`, `rules/testcase-generation.rules.md`, `schemas/testcase.schema.json`, `templates/testcase-template.json`, approved analysis | `testcase.json` |

If a task does not fit one of these routes, use only the supplied source and the minimum applicable rule. Do not imply that unsupported modules exist.

---

## 3. Analysis Contract

Analysis is the contract between raw-source understanding and test-case generation. It must be traceable to its source and must not add inferred behavior as fact.

`Raw source → DRAFT analysis → human review → APPROVED analysis → testcase.json`

An analysis must capture, when evidenced:

- source reference and summary
- screens or sections
- visible and interactive UI
- interactions and navigation
- states or variants
- requirements and business rules
- validation, error, loading, and success behavior
- dependencies and constraints
- unknowns, open questions, and source conflicts
- traceability/provenance

Generate test cases only from an `APPROVED` analysis. A `DRAFT` or `CHANGES_REQUESTED` analysis can be improved or reviewed, but is not a source contract for final test cases.

---

## 4. Test-Case Generation Contract

Use this route only when the requested deliverable is test cases.

### Required inputs

- `APPROVED` source analysis
- `skills/testcase-generation.skill.md`
- `rules/testcase-generation.rules.md`
- `schemas/testcase.schema.json`
- `templates/testcase-template.json`

### Required process

`Approved analysis → flow and UI inventory → scenarios → test cases → second coverage review → schema validation`

Cover supported positive and negative behavior, complete journeys, navigation, state changes, validation, alternate outcomes, retry/recovery, and meaningful dependencies. Apply exact boundary testing only when an exact source-supported limit exists.

### Field conventions

- `case` is only `Positive` or `Negative`.
- `pre_condition` contains state, access, data, or setup already true before Step 1. It must not hide user actions or navigation.
- `step` contains chronological, executable user/tester actions from the relevant entry point through the action that triggers the scenario outcome.
- `expected` contains observable system behavior, not repeated user actions.
- Expected results are Bahasa Indonesia unless the user requests another language.
- Gherkin must align with the scenario, steps, and expected result.
- Do not include execution results or evidence for unexecuted cases.

Before delivery, validate JSON against `schemas/testcase.schema.json` and perform the required second coverage review against the approved flow and UI inventory.

---

## 5. Output Rules

Preserve the supplied template and schema exactly. Do not add, remove, rename, or reorder fields unless the user explicitly requests it.

Current JSON contracts:

- Analysis: `schemas/analysis.schema.json`
- Test cases: `schemas/testcase.schema.json`

Current starting templates:

- Analysis: `templates/analysis-template.md`
- Analysis review: `templates/approval-template.md`
- Test cases: `templates/testcase-template.json`

Confirm each generated artifact exists, is readable, and matches the requested format before presenting it as complete.

---

## 6. Final Quality Gate

Before delivery, confirm:

- The correct current source was used.
- Only relevant modular files were loaded.
- Facts, interpretations, unknowns, and conflicts are clearly separated.
- No unsupported behavior or metadata was added.
- The relevant template and schema are preserved.
- The output is traceable to its source.
- Test cases, when generated, use approved analysis and passed the two-pass coverage review.

## 7. Maintenance

Keep this file as a lightweight router. Put detailed source-analysis methods in the relevant analysis skills and detailed test-case behavior in the test-case skill/rules. Avoid duplicating detailed rules here; update task-routing links when files are added, removed, or renamed.
