---
layout: post
title:  "Dispatch After Time using DispatchQueue"
date:   2017-10-31 10:00:00
categories: CodeSnippet
tags: DispatchQueue main async
comments: true
logo: refresh
---

### Swift Code Snippet

```swift
DispatchQueue.main.asyncAfter(deadline: .now() + 0.1) {
  // your code here
}
```

### Objective-C Code Snippet

```objective-c
var dispatchTime: dispatch_time_t = dispatch_time(DISPATCH_TIME_NOW, Int64(0.1 * Double(NSEC_PER_SEC)))
dispatch_after(dispatchTime, dispatch_get_main_queue(), {
  // your function here
})
```

### Example

```swift
func fetchStockData(_ handler: @escaping (([Stock]) -> Void)) {
	DispatchQueue.main.asyncAfter(deadline: .now() + .seconds(1)) {
		let stocks = StockManagerSDK.stockData()
		handler(stocks)
    }
}
```
