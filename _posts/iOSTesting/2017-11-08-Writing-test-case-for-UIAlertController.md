---
layout: post
title:  "Writing Test case for UIAlertController"
date:   2017-11-08 10:00:00
categories: CodeSnippet
tags: UIAlertView UIAlertController Test Testing XCTest TestCase 
comments: true
logo: wrench
---

### Code Snippet to show view controller

```swift
class MyCustomViewController: UIViewController {
  func showAlertView() {
    let title = "Title of the Alert"
    let message = "Message for Alert"
    let actions = [
      UIAlertAction(title: "Yes", style: UIAlertActionStyle.default, handler: { (action) in
        // piece of code if user taps on yes.
      }),
      UIAlertAction(title: "no", style: UIAlertActionStyle.default, handler: { (action) in
        // piece of code if user taps on no.
      }),
    ]
    let alert = UIAlertController(title: title, message: message, preferredStyle: UIAlertControllerStyle.alert)
      for action in actions {
        alert.addAction(action)
      }
      viewController.present(alert, animated: true, completion: nil)
  }
}
```

### Code Snippet to test above code

```swift
func testshowAlertView_DidShowValidAlert() {
  // SUT is System under test
  // here, SUT is an instance of 'MyCustomViewController'
  sut?.showAlertView()
  let exp = expectation(description: "Show AlertView Controller Expectation")
  DispatchQueue.main.asyncAfter(deadline: .now() + .seconds(1)) {
    // access root view controller
    let root = UIApplication.shared.keyWindow?.rootViewController

    // check if it presented AlertController or not
      XCTAssertTrue(root!.presentedViewController! is UIAlertController)

      // access alertController
      let alertController = root!.presentedViewController as! UIAlertController

      // Check if it has valid title or not
      XCTAssertEqual(alertController.title, "Title of the Alert")

      // Check if it has valid message or nots
      XCTAssertEqual(alertController.message, "Message for Alert")

      // Check if it has valid number of actions or not
      let actions = alertController.actions
      XCTAssertTrue(actions.count == 2)

      // Check if actions has valid titles or not
      XCTAssertEqual(actions[0].title, "Yes")
      XCTAssertEqual(actions[1].title, "No")
      exp.fulfill()
  }
  waitForExpectations(timeout: 5, handler: nil)
}
```