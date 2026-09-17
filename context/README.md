# QA Engineering ChatGPT Pack

This pack is the reusable QA Engineering Knowledge Base optimized for ChatGPT Projects.

## Structure

The pack separates responsibilities conceptually:

- `MASTER_INSTRUCTIONS.md` — routing, precedence, and global rules
- `QA_TEST_CASE_GENERATION.md` — test case generation skill + rules
- `AUTOMATION.md` — automation architecture skill/context/rules
- `MOBILE_AUTOMATION.md` — mobile Katalon/Appium context/skill/rules
- `JENKINS_CI_CD.md` — CI/CD context/skill/rules
- `REPORTING.md` — reporting and log analysis
- `DOCUMENTATION.md` — documentation and handover
- `AI_GENERATOR.md` — source-to-artifact AI workflow
- `FIGMA_WBS.md` — Figma/SVG to QA Automation WBS
- `TEMPLATES.md` — canonical test case and WBS output schemas
- `NAMING_AND_OUTPUT.md` — naming and file-output rules

## Recommended upload order

1. `MASTER_INSTRUCTIONS.md`
2. `QA_TEST_CASE_GENERATION.md`
3. `TEMPLATES.md`
4. `FIGMA_WBS.md`
5. `AUTOMATION.md`
6. `MOBILE_AUTOMATION.md`
7. `JENKINS_CI_CD.md`
8. `REPORTING.md`
9. `DOCUMENTATION.md`
10. `AI_GENERATOR.md`
11. `NAMING_AND_OUTPUT.md`

## Usage

Use the smallest relevant set for each task. Do not assume every document applies to every task.

The current source/requirement/design remains the primary source of truth. This pack provides reusable QA engineering behavior and constraints.

## Current QA Test Case Conventions

- Case: `Positive` / `Negative`
- Expected: Bahasa Indonesia unless explicitly requested otherwise
- Pre-condition: state/setup already true before execution
- Step: tester actions from the applicable entry point through the target outcome
- No invented requirements, limits, metadata, execution results, or evidence

## Current QA Automation WBS Conventions

Hierarchy:

`Squad → Big Feature → Epic / Feature → Story / Task → Sub_task`

Schema:

`Squad | Big Feature | Epic / Feature | Story / Task | Sub_task | Assignee | Status | Start Date | End Date`

`Squad`, `Assignee`, `Status`, `Start Date`, and `End Date` remain blank unless the source explicitly provides them.

## Maintenance

When a project-level rule changes, update the affected canonical file(s) and then synchronize dependent files such as `MASTER_INSTRUCTIONS.md`, `TEMPLATES.md`, and `README.md`.

Avoid accumulating duplicate or obsolete rules.
