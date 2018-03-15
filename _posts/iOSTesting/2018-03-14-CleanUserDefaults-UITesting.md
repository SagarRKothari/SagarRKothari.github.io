---
layout: post
title:  "Clear User defaults before launching XCUITests"
date:   2018-03-14 10:00:00
categories: CodeSnippet
tags: Testing Performance Xcode Test Testcase XCUI
comments: true
logo: anchor
---

Open your application delegate file & update `didFinishLaunching` method as follows.

```swift
private func resetStateIfUITesting() {
    // 3.
    if ProcessInfo.processInfo.arguments.contains("UI-Testing") {
        UserDefaults.standard.removePersistentDomain(forName: Bundle.main.bundleIdentifier!)
    }
}

// 1.
func application(_: UIApplication, didFinishLaunchingWithOptions _: [UIApplicationLaunchOptionsKey: Any]? = nil) -> Bool {
    resetStateIfUITesting() // 2.
```

- Step 1. Your application is launched.
- Step 2. It invokes a function named `resetStateIfUITesting` which is defined above here.
- Step 3. Function checks for process-argument named `UI-Testing`,
- Step 4. If it has such argument, it will clear user-defaults.

Question is how to pass such process-argument from XCUItests?

And here is the example for it.


```swift
import XCTest

class UITests: XCTestCase {
    private let app = XCUIApplication()

    override func setUp() {
        super.setUp()
        app.launchArguments += ["UI-Testing"]
        app.launch()
    }
}
```
