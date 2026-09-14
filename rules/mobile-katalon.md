# Rules: Mobile / Katalon

- Prefer Android `resource-id` and iOS `accessibility-id` when stable.
- Avoid absolute XPath and fragile hierarchy selectors.
- Use condition-based waits instead of fixed sleeps where possible.
- Keep scroll / swipe behavior scoped to the intended screen region.
- Verify device connectivity before debugging automation logic.
- Avoid repeated ADB pairing when an existing connection is valid.
- Keep platform-specific workarounds out of generic code unless they are genuinely reusable.
