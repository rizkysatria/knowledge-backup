# Context: Automation Architecture

## Established architecture

The preferred automation architecture is layered and feature-oriented:

`Feature → Step Definition → Usecase → Screen → Shared Automation Library → Automation Engine → Device`

The shared library is referred to as `ist-one-framework`.

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
