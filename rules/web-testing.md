# Rules: Web Testing

## 1. Web-specific coverage

When the target is a web application, include relevant web-specific behavior in addition to core functional UI coverage.

## 2. No unnecessary assumptions

Do not invent:
- Supported browsers
- Browser versions
- Responsive breakpoints
- Keyboard shortcuts
- Multi-tab behavior
- Accessibility requirements

Only test these when supported by the source, requirement, or observed application behavior.

## 3. Navigation

Where applicable, cover:
- Browser back / forward
- Refresh / reload
- Direct URL / deep link
- Redirect after success or failure
- Session behavior during navigation

## 4. Interaction

Where applicable, consider:
- Click
- Hover
- Keyboard input
- Tab navigation
- Focus changes
- Scroll
- Repeated interaction
- Disabled / enabled states

## 5. Browser compatibility

Browser compatibility is a separate coverage dimension from functional testing.

Add it only when supported browser scope is known.

## 6. Responsive behavior

Responsive coverage must be based on actual product requirements or source evidence.

Do not invent viewport sizes or breakpoint rules.

## 7. Accessibility

Include accessibility-related cases when accessibility is a stated requirement or materially evidenced by the source.

## 8. Separation from core QA coverage

Web-specific rules extend the core QA test case generation skill. They do not replace:
- Functional UI coverage
- Validation
- Negative testing
- Boundary testing
- State / transition coverage
- UAT
- SIT
- Security where relevant
- API / DB validation where available
