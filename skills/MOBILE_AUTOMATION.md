# Mobile Automation


## Context

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

`Feature → Step Definition → Usecase → Screen → Katalon/Appium → Device → Report`

Changes should be solved at the narrowest responsible layer.


## Mobile Katalon/Appium Skill

# Skill: Mobile Katalon / Appium

Use this skill for Android or iOS UI automation troubleshooting and implementation.

## Android

Prefer UiAutomator2 and stable identifiers such as `resource-id`.

For gesture behavior, use the most appropriate Appium mobile gesture command when supported by the environment. Keep gesture area and direction explicit.

For wireless debugging, verify existing pairing/connection before pairing again.

## iOS

Prefer XCUITest and stable `accessibility-id` values.

## Synchronization

Prefer condition-based waits such as element visibility / existence over fixed sleeps.

## Troubleshooting order

1. Verify device connection.
2. Verify Appium server / driver.
3. Verify app state.
4. Verify locator stability.
5. Verify synchronization.
6. Verify gesture / input behavior.
7. Only then change framework-level code.

Avoid platform-specific workarounds in shared core code unless the behavior is genuinely generic.


## Mobile Katalon Rules

# Rules: Mobile / Katalon

- Prefer Android `resource-id` and iOS `accessibility-id` when stable.
- Avoid absolute XPath and fragile hierarchy selectors.
- Use condition-based waits instead of fixed sleeps where possible.
- Keep scroll / swipe behavior scoped to the intended screen region.
- Verify device connectivity before debugging automation logic.
- Avoid repeated ADB pairing when an existing connection is valid.
- Keep platform-specific workarounds out of generic code unless they are genuinely reusable.


## Mobile Automation Quality Gate

Before finalizing a mobile automation change:
- Verify the target platform and driver.
- Verify device/app readiness.
- Prefer stable platform-native identifiers.
- Prefer condition-based synchronization.
- Keep platform-specific behavior scoped to the platform/screen that needs it.
