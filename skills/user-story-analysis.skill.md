# User Story Analysis Skill

## Purpose

Analyze a supplied User Story or user-story-like requirement source and convert it into a structured QA-relevant analysis.

The analysis must preserve the source intent while explicitly identifying information that is missing, ambiguous, or unsupported.

## Analyze

Analyze for:
- actor
- goal
- business intent
- acceptance criteria
- business rules
- preconditions
- primary flow
- alternate / exception flows
- dependencies
- constraints
- unknowns / open questions

## Rules

- Preserve the source wording and terminology where possible.
- Distinguish source-supported information from interpretation.
- Identify unsupported assumptions explicitly.
- Do not silently fill gaps with generic product or business assumptions.
- Do not invent UI, validation, calculations, limits, navigation, API behavior, technical implementation, or execution results unless supported by the source.
- Missing information must remain Unknown / Not Specified.
- The analysis is requirement interpretation only; it is not execution evidence.

## Output

Generate one analysis artifact:

`user-story-analysis-<feature>.md`

The result should contain, when applicable:
- Metadata / source reference
- Summary
- Actor
- Goal
- Business intent
- Primary journey / flow
- Acceptance criteria
- Business rules
- Preconditions
- Alternate / exception flows
- Dependencies / constraints
- Variants
- Unknowns / open questions
- Source traceability

Do not add sections that are not applicable merely to fill the template.

## Result

The generated `.md` is the analysis result used by downstream QA activities such as source synthesis.

It must reflect the supplied User Story or requirement source and must not introduce unsupported requirements.

## Quality Gate

Before completing the analysis:
- actor and goal are identified when supported
- the primary flow is captured
- acceptance criteria are preserved when present
- business rules are separated from assumptions
- alternate / exception flows are captured when supported
- dependencies and constraints are identified
- unknowns / open questions are explicit
- unsupported assumptions have not been converted into requirements
- source reference / traceability is preserved
