# Figma / SVG to WBS

## Context

# Context: Figma / SVG to WBS

Generate WBS items from Figma/SVG or equivalent UI sources specifically for QA Automation planning.

The design/source is evidence for:
- Features
- Screens
- Meaningful UI states
- Navigation
- User actions
- Forms
- Validation/error states when evidenced
- End-to-end flow relationships

Do not use an existing WBS as the source of truth unless the user explicitly asks for conformance to that WBS.

## Skill

# Skill: Figma / SVG to WBS

## Purpose

Generate a source-traceable QA Automation WBS from product requirements and UI/design sources such as Figma, SVG, screenshots, or equivalent artifacts.

## Required Hierarchy

Use:

`Squad → Big Feature → Epic / Feature → Story / Task → Sub_task`

### Big Feature
A larger product or business grouping explicitly supported by the source.

### Epic / Feature
The functional feature being automated under the Big Feature.

### Story / Task

When applicable, use:
- `Development <Feature>`
- `Integration <Feature>`
- `Locator <Feature>`

### Development / Screen

Decompose development work at screen level.

Use:
`Automation Screen <Screen Name>`

A screen-level item may represent a meaningful screen variant when the source clearly treats that variant as distinct automation work.

Do not create one ticket per button, text field, or minor UI element.

### Integration / Gherkin

Decompose meaningful end-to-end business flows.

Use:
`Gherkin Integration <Flow Name>`

Integration items should represent a complete meaningful flow, not an isolated screen.

### Locator / Object ID

Decompose automation-relevant locator work.

Use:
`Object ID <Screen / Component Name>`

Group locators at a useful automation boundary. Do not create one WBS ticket per individual locator unless the source/project explicitly requires that granularity.

## Source Analysis

Before generating:
1. Identify the Big Feature and Epic / Feature from the source.
2. Inventory screens and meaningful variants.
3. Identify navigation and user actions.
4. Identify meaningful states and validation/error states when evidenced.
5. Identify complete E2E relationships.
6. Map each source element to the appropriate WBS level.

## Rules

### Source of Truth
- Use current PRD, user story, Figma/SVG, screenshots, or equivalent source evidence.
- Do not copy an existing WBS as content unless explicitly requested.
- Preserve source terminology where practical.
- Do not invent functionality, screens, flows, or metadata.

### Metadata
Keep these blank when not explicitly supported:
- Squad
- Assignee
- Status
- Start Date
- End Date

Do not infer `Squad` from an existing example.

### Variants
Create separate screen/flow items only when the source provides evidence that they represent meaningful distinct automation work. Otherwise group them at the appropriate level.

### Traceability
Every Sub_task should be traceable to a source screen, component grouping, or meaningful E2E flow.

### Quality Gate
Before delivery verify:
- Required hierarchy is present.
- Every relevant source screen is accounted for.
- Meaningful variants are not silently omitted.
- Integration items represent real E2E flows.
- Locator work is separated from screen implementation.
- No unsupported business behavior or metadata was invented.
- The WBS schema matches the required template exactly.

## WBS Rules

# Rules: WBS

- Preserve the exact requested column order.
- Use the 9-column QA Automation schema when using the current QA Pack template:
  `Squad | Big Feature | Epic / Feature | Story / Task | Sub_task | Assignee | Status | Start Date | End Date`
- Keep `Squad` blank unless provided.
- Keep metadata blank unless provided.
- Keep Development, Integration, and Locator work distinct.
- Use screen-level Development items.
- Use meaningful E2E Integration items.
- Use automation-relevant Locator items.
- Do not make one ticket per button/field by default.
- Do not copy example WBS content into a new source-derived WBS.
- Preserve source-derived ordering where it improves traceability.
