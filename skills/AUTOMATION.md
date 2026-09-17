# Automation Engineering


## Context

# Context: Automation Architecture

## Established architecture

The preferred automation architecture is layered and feature-oriented:

`Feature → Step Definition → Usecase → Screen → Automation Engine → Device`

## Layer responsibilities

### Feature
Business-readable Gherkin scenarios.

### Step Definition
Thin mapping from Gherkin to Usecase methods.

### Usecase
Business flow and orchestration. Avoid screen-specific locator knowledge.

### Screen
Screen-specific UI interaction and locator knowledge.

### Shared Automation Library
Reusable technical capabilities such as UIAction, UIAssert, Wait, Swipe, Logger, and Utilities.

## Design principles

- Separation of concern
- Single responsibility
- Reusability
- Maintainability
- Scalability
- Minimal duplication
- One-way dependency flow

Prefer solving changes at the correct layer instead of modifying shared core behavior for a feature-specific need.


## Architecture Skill

# Skill: Automation Architecture

Design automation using clear layer boundaries and reusable components.

## Layer

`Feature → Step Definition → Usecase → Screen → Automation Engine → Device`

## Responsibilities

- Feature: business-readable behavior.
- Step Definition: thin BDD mapping.
- Usecase: business flow / orchestration.
- Screen: UI behavior and locators.

## Rules of design

- Keep dependencies one-way.
- Keep business logic out of generic framework utilities.
- Keep locators out of Usecase.
- Avoid duplicated technical logic across Screens.
- Prefer configuration over hardcoded environment values.
- Solve change at the narrowest responsible layer.
- Keep reusable functionality generic enough to be safely shared.


## Automation Rules

# Rules: Automation

- Keep Feature, Step Definition, Usecase, Screen, and shared framework responsibilities separate.
- Keep business flow out of shared generic utilities.
- Keep locator knowledge in Screen-level code.
- Prefer reusable helpers over duplicate implementation.
- Use stable locators.
- Keep environment-specific values configurable.
- Do not change shared core behavior for a feature-specific problem unless the behavior is truly generic.


## Change / Troubleshooting Quality Gate

Before changing shared framework code:
1. Confirm the issue is reproducible.
2. Verify the device/application/environment state.
3. Verify the Screen-level implementation and locator.
4. Verify synchronization and gesture/input handling.
5. Determine the narrowest responsible layer.