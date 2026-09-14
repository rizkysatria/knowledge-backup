# Context: Mobile Automation

## Platforms

Primary mobile targets:
- Android
- iOS

Common stack:
- Katalon Studio
- Appium
- UiAutomator2 for Android
- XCUITest for iOS
- Groovy
- Real devices and simulators/emulators

## Mobile-specific behavior

Consider:
- Tap, long press, swipe, and scroll behavior
- Keyboard and custom keyboard behavior
- Native dialogs and permission prompts
- App background / foreground transitions
- Orientation changes
- Network changes
- Device-specific rendering and behavior
- Accessibility labels / resource identifiers
- Element visibility after scrolling

## Locator preference

Prefer stable identifiers exposed by the application:
- Android: `resource-id` where available
- iOS: `accessibility-id` where available

Avoid absolute XPath and fragile hierarchy-based locators.

## Automation architecture context

The established layered flow is:

`Feature → Step Definition → Usecase → Screen → ist-one-framework → Katalon/Appium → Device → Report`

Changes should be solved at the narrowest responsible layer.
