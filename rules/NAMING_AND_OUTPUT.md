# Naming & Output Rules


## Naming Rules

# Rules: Naming

Use clear, consistent, descriptive names.

Established automation naming:
- Groovy Screen: `PascalCase<Screen>.groovy`
- Python / Playwright Screen: `kebab-case-<screen>-screen.py`

Do not encode product-specific names into generic rules unless explicitly required by the current project.


## File Output Rules

# Rules: File Output

- Preserve the requested output format.
- Keep generated files directly usable by the target tool.
- Use timestamped output names when the workflow requires versioned artifacts.
- Validate that the output file exists and is readable before delivery.
- Never present a file as complete if key content failed to generate.


## QA Artifact Naming

Use clear, descriptive, task-oriented names.

Recommended generated artifact names:
- Test Case: `TC_<Feature>_<Platform>.xlsx`
- QA Automation WBS: `WBS_<Feature>_QA_Automation.xlsx`

Do not add dates or versions unless versioning is explicitly required by the workflow.

## Output Validation

Before delivery:
- Confirm the file exists.
- Confirm the file is readable/openable.
- Confirm the schema matches the requested template.
- Confirm execution-only fields are blank when the artifact is unexecuted.
- Confirm no required source-derived content was omitted.
