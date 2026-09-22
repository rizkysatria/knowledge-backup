# Figma / SVG Analysis Skill

## Purpose

Analyze supplied Figma-derived source or SVG for QA-relevant evidence.

The analysis must describe what is supported by the source without inventing business rules, behavior, or implementation details.

## Analyze

Capture:
- screens and sections
- visible text and UI labels
- interactive-looking controls
- component relationships
- variants / states visible in the source
- navigation evidence
- loading, error, empty, success, disabled, selected, expanded/collapsed states when evidenced
- unknowns / open questions

## Rules

- Preserve source terminology where possible.
- Distinguish observed visual evidence from interpretation.
- Do not infer business rules solely from visual appearance.
- Do not invent validation, calculations, required/optional behavior, navigation, API behavior, or technical implementation when unsupported by the source.
- Treat missing visual evidence as Unknown / Not Specified, not as evidence that the behavior does not exist.
- For large SVGs, prefer deterministic preprocessing before semantic interpretation.
- The analysis is source analysis only; it is not execution evidence.

## Output

Generate one analysis artifact:

`figma-analysis-<feature>.md`

The result should contain, when applicable:
- Metadata / source reference
- Screens / sections
- UI / component inventory
- Variants / states
- Navigation evidence
- Unknowns / open questions
- Source traceability

Do not add sections that are not applicable merely to fill the template.

## Result

The generated `.md` is the analysis result used by downstream QA activities such as source synthesis.

It must reflect only evidence supported by the supplied Figma-derived source or SVG.

## Quality Gate

Before completing the analysis:
- relevant screens and sections have been considered
- visible UI evidence has been captured
- evidenced states and variants have been captured
- navigation evidence is separated from assumptions
- unknowns are explicitly recorded
- unsupported business rules or behavior have not been invented
- source reference / traceability is preserved
