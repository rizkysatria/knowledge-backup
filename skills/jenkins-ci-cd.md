# Skill: Jenkins CI/CD

Design automation execution so it is repeatable, configurable, observable, and safe for parallel runs.

## Execution flow

`Checkout → Prepare Environment → Device Readiness → App Readiness → Automation Execution → Report → Cleanup`

## Practices

- Keep environment values configurable.
- Avoid redundant checkout/setup when the pipeline design permits reuse.
- Validate device readiness before running tests.
- Avoid duplicate ADB pairing when a valid connection already exists.
- Use unique resources for parallel devices.
- Preserve logs and reports for troubleshooting.
- Fail fast on environment readiness failures when continuing would produce misleading results.
