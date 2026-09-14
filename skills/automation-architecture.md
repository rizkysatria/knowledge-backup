# Skill: Automation Architecture

Design automation using clear layer boundaries and reusable components.

## Layer

`Feature → Step Definition → Usecase → Screen → ist-one-framework → Automation Engine → Device`

## Responsibilities

- Feature: business-readable behavior.
- Step Definition: thin BDD mapping.
- Usecase: business flow / orchestration.
- Screen: UI behavior and locators.
- `ist-one-framework`: generic reusable technical capabilities.

## Rules of design

- Keep dependencies one-way.
- Keep business logic out of generic framework utilities.
- Keep locators out of Usecase.
- Avoid duplicated technical logic across Screens.
- Prefer configuration over hardcoded environment values.
- Solve change at the narrowest responsible layer.
- Keep reusable functionality generic enough to be safely shared.
