# Context: Web Testing

## Purpose

Web-specific context for QA test case generation and web UI validation.

## Web-specific behavior

Consider when applicable:
- Mouse click and interaction behavior
- Hover behavior
- Keyboard input and keyboard navigation
- Tab order and focus behavior
- Browser back / forward navigation
- Page refresh / reload behavior
- URL and deep-link navigation
- Multiple tabs / windows
- Browser dialogs where applicable
- File upload / download behavior
- Session, cookie, and authentication state
- Responsive viewport behavior
- Browser-specific rendering and behavior
- Element visibility after scrolling
- Accessibility labels and keyboard accessibility

## UI coverage

For web UI, consider:
- Headers and navigation
- Forms and form controls
- Tables and row actions
- Search, filter, sort, and pagination
- Tabs
- Modals / dialogs
- Tooltips / hover states
- Toasts / alerts
- Loading indicators
- Empty states
- Error / success messages
- Sticky or fixed actions

## Browser compatibility

Only add browser compatibility coverage when supported browsers are defined by the requirement or project source.

Do not invent browser versions or supported-browser requirements.

## Responsive behavior

Only add responsive coverage when responsive behavior is relevant to the product or source.

Do not assume specific breakpoints or device sizes when they are not defined.
