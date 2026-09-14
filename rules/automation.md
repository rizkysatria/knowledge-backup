# Rules: Automation

- Keep Feature, Step Definition, Usecase, Screen, and shared framework responsibilities separate.
- Keep business flow out of shared generic utilities.
- Keep locator knowledge in Screen-level code.
- Prefer reusable helpers over duplicate implementation.
- Use stable locators.
- Keep environment-specific values configurable.
- Do not change shared core behavior for a feature-specific problem unless the behavior is truly generic.
