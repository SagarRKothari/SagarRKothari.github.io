---
layout: post
title:  "Get Tomorrow Date or add a date to given date"
date:   2017-10-20 13:00:00
categories: CodeSnippet
tags: NSDate Date Tomorrow
comments: true
logo: calendar-plus-o
---

```swift
func getTomorrowDate() -> Date {
  let cal = NSCalendar.current
  let now = Date()
  let compSet = Set(arrayLiteral:Calendar.Component.day,
                    Calendar.Component.month,
                    Calendar.Component.year)
  var comp = cal.dateComponents(compSet as Set<Calendar.Component>, from: now)
  comp.timeZone = TimeZone.current
  comp.day = comp.day! + 1
  return cal.date(from: comp)!
}
```