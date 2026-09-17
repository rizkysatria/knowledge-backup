# QA Pack Update Manifest

Updated: 2026-09-17

## Main synchronization changes

- Removed the deprecated `Regression UAT` test-case field/rule.
- Standardized Case to `Positive` / `Negative`.
- Standardized Expected Result language to Bahasa Indonesia unless explicitly requested otherwise.
- Clarified Pre-condition vs Step responsibilities.
- Canonicalized current Mobile and Web test-case templates.
- Canonicalized QA Automation WBS hierarchy:
  `Squad → Big Feature → Epic / Feature → Story / Task → Sub_task`
- Canonicalized current 9-column WBS schema:
  `Squad | Big Feature | Epic / Feature | Story / Task | Sub_task | Assignee | Status | Start Date | End Date`
- Explicitly prohibited inferred Squad/Assignee/Status/Date metadata.
- Clarified that new WBS must be source-derived and must not silently copy an existing WBS.
- Synchronized README, MASTER_INSTRUCTIONS, TEMPLATES, FIGMA_WBS, and AI_GENERATOR routing.
- Preserved the existing automation architecture and mobile/Jenkins/reporting/documentation guidance, while adding aligned quality gates.
