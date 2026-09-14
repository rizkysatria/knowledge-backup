# Skill: Reporting / Dashboard / Log Analysis

Separate the process into:

`Parse → Normalize → Map → Calculate → Present`

## Inputs

- JUnit XML
- Katalon CSV
- Execution logs
- Device / ADB logs
- API logs

## Metrics

Calculate from actual evidence:
- Total
- Passed
- Failed
- Skipped
- Pass rate
- Failure rate
- Flaky rate when evidence supports it

## Analysis

Support breakdowns by feature, sub-feature, test case, environment, and failure reason when available.

Never fabricate missing data. Distinguish parsing failures from test failures.
