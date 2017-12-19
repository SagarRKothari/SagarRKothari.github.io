---
layout: post
title:  "Performance Testing with measure block - Xcode"
date:   2017-11-19 10:00:00
categories: CodeSnippet
tags: Testing Performance Xcode Test Testcase Unit
comments: true
logo: anchor
---

For performance testing, Xcode provides measure block with the help of which we can execute performance testing.

The measured block is executed ten times and the test output shows the average execution time as well as individual run times and standard deviation:

```swift
func testDateFormatterPerformance() {
  let dateFormatter = DateFormatter()
  dateFormatter.dateStyle = .long
  dateFormatter.timeStyle = .short
  
  let date = Date()
  
  measure {
    let string = dateFormatter.string(from: date)
    print(string)
  }
}
```

![Step 0]({{"assets/2017-11-19/Step0.png" | absolute_url}})

Click on the gray button, once you're done executing test case.
It will open pop-over and show the results of those 10 executions.

![Step 1]({{"assets/2017-11-19/Step1.png" | absolute_url}})

<br>

![Step 2]({{"assets/2017-11-19/Step2.png" | absolute_url}})

