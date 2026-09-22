# PRD Analysis Skill

## Purpose

Analyze a supplied PRD and convert its supported product requirements into a structured QA-relevant analysis.

The analysis must preserve the PRD's scope and terminology while explicitly identifying missing, ambiguous, or unsupported information.

## Analyze

Analyze for:
- feature scope
- functional requirements
- non-functional requirements when present
- business rules
- dependencies
- constraints
- acceptance criteria
- primary flows
- alternate / error conditions
- variants when explicitly defined
- open questions / unknowns

## Rules

- Preserve PRD terminology where possible.
- Distinguish explicit requirements from interpretation.
- Do not silently fill gaps with generic product assumptions.
- Do not invent UI, validation, calculations, limits, navigation, API behavior, technical implementation, or execution results unless supported by the PRD.
- Treat missing information as Unknown / Not Specified.
- Non-functional requirements should only be captured when present in the source.
- The analysis is requirement analysis only; it is not execution evidence.

## Output

Generate one analysis artifact:

`prd-analysis-<feature>.md`

The result should contain, when applicable:
- Metadata / source reference
- Scope
- Functional requirements
- Non-functional requirements
- Business rules
- Primary flows
- Acceptance criteria
- Alternate / error conditions
- Dependencies / constraints
- Variants
- Unknowns / open questions
- Source traceability

Do not add sections that are not applicable merely to fill the template.

## Result

The generated `.md` is the analysis result used by downstream QA activities such as source synthesis.

It must reflect the supplied PRD and must not introduce unsupported product requirements.

## Quality Gate

Before completing the analysis:
- scope is captured
- functional requirements are identified
- non-functional requirements are captured only when supported
- business rules are separated from assumptions
- acceptance criteria are preserved when present
- alternate / error conditions are captured when supported
- dependencies and constraints are identified
- unknowns / open questions are explicit
- unsupported assumptions have not been converted into requirements
- source reference / traceability is preserved
