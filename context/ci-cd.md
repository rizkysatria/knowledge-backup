# Context: CI/CD

Typical automation CI/CD stack:
- Git / Bitbucket
- Jenkins
- Katalon Runtime / Katalon execution
- Android SDK / ADB
- Appium
- Real devices

Environment-specific values such as device identifiers, ports, credentials, project IDs, and app paths should be configurable rather than hardcoded.

Parallel execution requires clear device identity, isolated execution context, and collision-safe resources.
