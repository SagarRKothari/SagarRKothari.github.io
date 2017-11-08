---
layout: post
title:  "Animate view on updating constraint values"
date:   2017-11-08 12:00:00
categories: CodeSnippet
tags: UIView Animation Animate Constraint
---

Add following method inside your `view controller`.

```swift
func animateListView() {
  view.setNeedsUpdateConstraints()
  UIView.animate(withDuration: 0.25, animations: {
    self.view.layoutIfNeeded()
  }, completion: nil)
}
```

After updating constraint value, invoke above method.