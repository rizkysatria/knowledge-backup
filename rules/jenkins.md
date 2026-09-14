# Rules: Jenkins

- Configuration must be externalized or parameterized.
- Do not hardcode credentials or secrets.
- Validate device readiness before execution.
- Parallel executions must use isolated resources.
- Do not allow stale device state to be mistaken for a test failure.
- Preserve execution logs and reports.
