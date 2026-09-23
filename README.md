# QA Project Knowledge Pack

Modular QA knowledge pack for source analysis, source synthesis, test case generation, and QA Automation WBS generation.

## Core Flow

```text
                                    
┌─────────────────────┐                     ┌─────────────────────┐      
│   User Story / PRD  │                     │      Figma / SVG    │   
└──────────┬──────────┘                     └──────────┬──────────┘
           ↓                                           ↓        
prd-analysis.skill.md                        figma-analysis.skill.md
           ↓                                           ↓
user-story-analysis.skill.md                    figma-analysis.md
           ↓                                           │
user-story-analysis.md                                 │
           │                                           │
           └────────────┬──────────────────────────────┘
                        ↓
             source-synthesis.skill.md
                        ↓
             source-synthesis.md
                        ↓
                   [ APPROVED ]
                        │
               ┌────────┴────────┐
               ↓                 ↓
      testcase-generation     wbs-generation
      skill + rules           skill + rules
               ↓                 ↓
         testcase.json         WBS.xlsx
```

## Source Analysis

Raw product sources are analyzed before any downstream QA artifact is generated.

### Figma / SVG

```text
Figma / SVG
    ↓
skills/figma-analysis.skill.md
    ↓
rules/source-analysis.rules.md
    ↓
schemas/analysis.schema.json
    ↓
figma-analysis-<feature>.md
```

The analysis captures source-supported screens, UI elements, states, variants, navigation evidence, and unknowns without inventing unsupported behavior.

### User Story / PRD

```text
User Story / PRD
    ↓
skills/user-story-analysis.skill.md
or
skills/prd-analysis.skill.md
    ↓
rules/source-analysis.rules.md
    ↓
schemas/analysis.schema.json
    ↓
user-story-analysis-<feature>.md
or
prd-analysis-<feature>.md
```

The analysis captures requirements, user goals, journey, acceptance behavior, business rules, validation, dependencies, variants, and unknowns supported by the source.

## Source Synthesis

When multiple source analyses are available, combine them before downstream generation.

```text
figma-analysis.md
        +
user-story-analysis.md
        +
other source analyses
        ↓
skills/source-synthesis.skill.md
        ↓
rules/source-analysis.rules.md
        ↓
schemas/analysis.schema.json
        ↓
source-synthesis-<feature>.md
        ↓
[ APPROVED ]
```

Source synthesis preserves provenance, conflicts, ambiguities, unknowns, and QA readiness. It becomes the source-of-truth analysis for downstream generation.

## Test Case Generation

Test cases are generated from an **APPROVED analysis**, not directly from raw Figma, User Story, or PRD files.

```text
APPROVED analysis
        ↓
skills/testcase-generation.skill.md
        ↓
rules/testcase-generation.rules.md
        ↓
schemas/testcase.schema.json
        ↓
templates/testcase-template.json
        ↓
testcase.json
```

### Test Case Principles

- Every testcase is independently executable.
- Step starts from the applicable journey entry point and includes the required navigation and actions.
- Pre-condition contains only state, data, access, configuration, or setup already true before execution.
- Expected contains observable system behavior.
- Gherkin represents reusable business behavior and remains aligned with Scenario, Step, and Expected.
- Positive and negative coverage is generated only from supported source behavior.
- A second coverage review is performed before delivery.

## WBS Generation

WBS is a separate downstream artifact for QA Automation planning.

```text
APPROVED analysis / applicable source
        ↓
skills/wbs-generation.skill.md
        ↓
rules/wbs-generation.rules.md
        ↓
WBS schema / template
        ↓
WBS.xlsx
```

Required hierarchy:

```text
Squad
  ↓
Big Feature
  ↓
Epic / Feature
  ↓
Story / Task
  ↓
Sub_task
```

## Knowledge Base Structure

```text
.
├── README.md
├── QA_INSTRUCTIONS.md
│
├── skills/
│   ├── figma-analysis.skill.md
│   ├── prd-analysis.skill.md
│   ├── user-story-analysis.skill.md
│   ├── source-synthesis.skill.md
│   ├── testcase-generation.skill.md
│   └── wbs-generation.skill.md
│
├── rules/
│   ├── source-analysis.rules.md
│   ├── testcase-generation.rules.md
│   └── wbs-generation.rules.md
│
├── schemas/
│   ├── analysis.schema.json
│   └── testcase.schema.json
│
└── templates/
    ├── analysis-template.md
    ├── approval-template.md
    └── testcase-template.json
```

## Routing Principle

Load only the files required for the current task.

```text
Identify Task
     ↓
Identify Source of Truth
     ↓
Load Relevant Skill
     ↓
Load Relevant Rules
     ↓
Load Schema / Template
     ↓
Analyze
     ↓
Validate
     ↓
Generate
     ↓
Review
     ↓
Output
```

The current source or requirement remains the source of truth. Skills define how a task is performed, rules define mandatory constraints and quality gates, and schemas/templates define the expected output structure.

## Important Boundary

```text
Raw Source
    ↓
Analysis
    ↓
Human Review / Approval
    ↓
Approved Analysis
    ↓
Test Case / WBS Generation
```

Do not skip the analysis layer when the task requires source understanding. Do not generate unsupported requirements, behavior, validation, metadata, or execution results.
