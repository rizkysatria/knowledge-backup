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
