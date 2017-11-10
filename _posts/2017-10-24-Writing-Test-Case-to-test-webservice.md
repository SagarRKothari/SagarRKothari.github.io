---
layout: post
title:  "Writing Test cases to test web service"
date:   2017-10-24 10:00:00
categories: CodeSnippet
tags: XCTest testing test expectation fulfill
comments: true
---

### Put following swift test function and replace with your web-service call code.

```swift
func testSomeWebService() {
  // create expectation
  let exp = expectation(description: "Some web service expectation")
  DispatchQueue.main.asyncAfter(deadline: .now() + .seconds(1)) {
    // got response
    exp.fulfill()
  }
  waitForExpectations(timeout: 30, handler: nil)
}
```

