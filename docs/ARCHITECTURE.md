# QA Test Case Pipeline Architecture

## Goal
Separate source understanding from test case generation so that the model does not need to repeatedly reason over large raw design/source files.

## Pipeline

SOURCE
  -> SOURCE ANALYSIS
  -> analysis.md
  -> HUMAN REVIEW
  -> APPROVED
  -> TEST CASE GENERATION
  -> testcase.json

## Responsibilities

### Source Analysis
Extract and structure only what is supported by the source:
- screens / sections
- visible and interactive UI elements
- labels and text
- navigation evidence
- states / variants
- requirements and business rules when present
- validation / error / success evidence
- dependencies and constraints
- unknowns / unresolved items
- source provenance

### Human Review
The reviewer checks the analysis against the original source and either approves it or requests changes.

Recommended status values:
- DRAFT
- CHANGES_REQUESTED
- APPROVED

Test case generation should use APPROVED analysis as its primary source contract.

### Test Case Generation
Generate test cases from approved analysis plus the applicable QA test-case rules, schema, and template. Do not invent unsupported behavior.

## Separation Principle
- Rules define constraints.
- Skills define task-specific reasoning.
- Schemas define machine-readable output contracts.
- Templates define human-readable starting formats.
- Tools perform deterministic preprocessing.
- Source files remain task-specific inputs.
