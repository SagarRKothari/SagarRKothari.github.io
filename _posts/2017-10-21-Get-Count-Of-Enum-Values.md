---
layout: post
title:  "Get Count of Swift Enum Values"
date:   2017-10-21 13:00:00
categories: CodeSnippet
tags: Enum Enumeration Count Total 
comments: true
logo: arrows-alt
---

In following enum example, I have added a static variable named `count` which calculates and returns count of the given enum.

```swift
enum ToDoPriority: Int {
  case High
  case Medium
  case Low
  var stringValue: String {
    switch self {
    case .High:
      return "High"
    case .Medium:
      return "Medium"
    case .Low:
      return "Low"
    }
  }
  static let count: Int = {
    var max: Int = 0
    while let _ = ToDoPriority(rawValue: max) { max += 1 }
    return max
  }()
}
```