---
layout: post
title:  "Writing Test cases to test web service"
date:   2017-10-24 10:00:00
categories: CodeSnippet
tags: XCTest testing test expectation fulfill
comments: true
logo: plug
---

### Put following swift test function and replace with your web-service call code.

```swift
func testWebService() {
  let string = "http://www.mocky.io/v2/5a1409093100002923b33fc0"
  // create expectation
  let exp = expectation(description: "Some web service expectation")
  let task = URLSession.shared.dataTask(with: URL(string: string)!) { (data, response, error) in
    if error != nil && data != nil && data!.count > 0 {
      exp.fulfill()
    } else {
      XCTFail("Webservice failed.")
    }
  }
  task.resume()
  waitForExpectations(timeout: 30, handler: nil)
}
```

Here is another example.

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