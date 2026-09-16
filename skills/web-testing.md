# Skill: Web Testing

## Purpose

Apply web-specific QA coverage when generating or reviewing test cases for web applications.

## Workflow

Use the core QA test case generation workflow first:

`Source → Flow Map → UI Inventory → Interaction Map → State Map → Test Cases → Coverage Review`

Then add relevant web-specific coverage.

## Web interaction coverage

For each relevant web interaction, consider:
- Initial state
- Click / primary interaction
- Result of interaction
- State after interaction
- Repeated interaction
- Change / reselection
- Invalid interaction
- Interaction after an error
- Interaction after success
- Impact on the next step

## Navigation coverage

Where applicable:
- Entry point
- Internal navigation
- Browser back
- Browser forward
- Refresh / reload
- Cancel / close
- Redirect
- Direct URL / deep link

## Form coverage

Where applicable:
- Empty input
- Valid value
- Invalid format
- Special characters
- Whitespace
- Leading / trailing whitespace
- Boundary values
- Paste / replacement
- Keyboard input
- Validation error
- Recovery after validation failure

## Web-specific UI states

Where applicable:
- Hover
- Focus
- Disabled
- Loading
- Empty state
- Error state
- Success state
- Modal / dialog
- Toast / alert
- Tooltip
- Sticky / fixed controls
- Scroll-dependent visibility

## Browser / responsive / accessibility coverage

Add these dimensions only when supported by requirements, source evidence, or observed application behavior.

### Browser compatibility

Validate supported browser behavior without inventing unsupported browser/version combinations.

### Responsive behavior

Validate defined responsive behavior without inventing breakpoints or viewport requirements.

### Accessibility

Validate relevant accessibility behavior when accessibility requirements or evidence exist.

## File handling

For web file upload/download flows, include relevant validation, failure, retry, replacement, and recovery scenarios.

Use the dedicated file-upload testing skill when the feature involves file uploads.

## Final review

After generating cases:

`Generated Cases → Web UI Inventory → User Flow → Web Interaction Coverage → SIT/UAT Coverage → Gap Review`

The second-pass review remains mandatory.
