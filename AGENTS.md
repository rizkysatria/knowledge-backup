# QA Engineering Pack — Agent Instructions

## Purpose

This repository is the reusable QA Engineering knowledge base for agent-based QA work.

## Rule Precedence

Apply precedence in this order:

1. Explicit current user instruction
2. Current task source / requirement / design / application behavior
3. Applicable project context
4. QA Pack knowledge base
5. Generic domain assumptions

Never invent requirements, UI behavior, business rules, exact validation limits, screens, flows, test results, evidence, metadata, or implementation details.

## Repository Structure

- `rules/` — mandatory constraints, standards, quality gates, routing, naming, and task-specific rules.
- `skills/` — task-specific methods and generation/engineering guidance.
- `templates/` — canonical output schemas and templates.
- `context/` — QA Pack background/context material.

## Loading Strategy

Read `rules/MASTER_INSTRUCTIONS.md` first. Then load only the files relevant to the current task.

### Create Test Case

Load:

- `rules/MASTER_INSTRUCTIONS.md`
- `rules/CREATE_TEST_CASE_RULES.md`
- `skills/QA_TEST_CASE_GENERATION.md`
- `skills/AI_GENERATOR.md`
- `templates/TEMPLATES.md`
- Current task source / requirement / design

### WBS / Figma / SVG

Load the applicable WBS skill and template plus the current source.

### Automation / Mobile Automation

Load the applicable automation skill, mobile skill, rules, naming/output guidance, and current source.

## Test Case Contract

For every test case:

`Entry Point → Full Required Journey → Target Action → Expected Outcome`

Step must start from the applicable journey entry point and include all source-defined navigation and user actions required to reach the target scenario. Do not shortcut the journey.

Pre-condition contains only state/data/setup already true before execution.

Expected contains the observable system result/behavior caused by the Step and is written in Bahasa Indonesia unless explicitly requested otherwise.

Before delivery, perform the required second coverage review and validate the applicable template/schema.

## General Agent Rules

- Use the current task source as the primary source for task-specific behavior.
- Keep business behavior separate from implementation details.
- Preserve canonical templates and schemas.
- Keep execution-only fields blank for unexecuted cases.
- Do not use an existing artifact as a hidden content template unless explicitly requested.
- Prefer the narrowest responsible layer when changing automation behavior.

## Maintenance

When a canonical rule changes, update dependent references consistently. Avoid duplicate or contradictory rules.
