# QA Engineering Knowledge Base

Read this file first.

## Purpose

This repository is a reusable QA engineering knowledge base for generating test cases, designing automation, analyzing automation results, documenting frameworks, and supporting AI-assisted QA workflows.

## How to use the knowledge base

1. Identify the task.
2. Load only the relevant context.
3. Load the relevant skill(s).
4. Load the relevant rule(s).
5. Use the applicable template when one exists.
6. Generate the output.
7. Run the relevant validation / quality gate before finalizing.

## Layer responsibilities

- `context/` = background knowledge and established project-agnostic engineering context.
- `skills/` = how to perform a task.
- `rules/` = mandatory constraints, standards, and quality gates.
- `templates/` = expected output structure.

## Core principles

- Use the provided source as the primary source of truth.
- Do not invent requirements, UI behavior, test results, data, or implementation details.
- Prefer complete meaningful coverage over a large number of shallow test cases.
- Keep responsibilities separated and reusable.
- Preserve user-provided templates unless a redesign is explicitly requested.
- Keep artifacts traceable to their source.
- When information is missing, mark it as unknown or requirement-dependent instead of guessing.

## Task routing

### Test case generation

Read:
- `context/qa-engineering.md` when general QA context is needed.
- `context/mobile-automation.md` for mobile-specific behavior.
- `skills/qa-test-case-generation.md`.
- `rules/qa-test-case-generation.md`.
- `templates/test-case-template.md` when an output template is required.

### Automation design / implementation

Read:
- `context/automation-architecture.md`.
- `context/mobile-automation.md` for mobile work.
- `skills/automation-architecture.md` and/or `skills/mobile-katalon-appium.md`.
- `rules/automation.md` and applicable platform rules.

### CI/CD

Read:
- `context/ci-cd.md`.
- `skills/jenkins-ci-cd.md`.
- `rules/jenkins.md`.

### Reporting / log analysis

Read:
- `context/reporting.md`.
- `skills/reporting-dashboard-log-analysis.md`.
- `rules/reporting.md`.

### Documentation / handover

Read:
- `context/documentation.md`.
- `skills/documentation-handover.md`.
- `rules/documentation.md`.

### AI automation / source-to-artifact workflow

Read:
- `context/ai-generator.md`.
- `skills/ai-automation-generator.md`.
- applicable AI rules.

### Figma / SVG to WBS

Read:
- `skills/figma-to-wbs.md`.
- `rules/ai-generator.md` where applicable.
- `templates/wbs-output-template.md`.

## Precedence

Use this order when sources conflict:

1. Explicit current user instruction.
2. Current task source / requirement / design / application behavior.
3. Applicable project context explicitly supplied for the task.
4. This knowledge base.
5. Generic domain assumptions.

Never use a generic assumption to override explicit source evidence.
