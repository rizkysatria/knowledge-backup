# Skill: Figma / SVG to WBS

Generate a WBS from a Figma/SVG design or equivalent UI source for automation planning.

## Analysis

Identify:
- Features
- Screens
- Meaningful UI states
- Navigation
- User actions
- Forms
- Validation / error states when evidenced
- End-to-end flow relationships

## Work decomposition

Use three work categories when the project template requires them:

1. Screen / Development
2. Object ID / Locator
3. Gherkin Integration

A Screen work item is screen-level, not one ticket per button or field.

Object ID work maps to automation-relevant screens.

Gherkin Integration represents a complete meaningful E2E business flow, not an isolated screen.

## Evidence rules

- Use names from the current design/source.
- Do not invent business flows.
- Do not invent assignees, dates, or statuses.
- Keep the WBS traceable to the source.
- Preserve the provided WBS column schema and hierarchy.
