---
layout: post
title:  "UIView Flip Animation Code"
date:   2017-11-02 10:00:00
categories: CodeSnippet
tags: UIView Flip Animation Code
comments: true
logo: unsorted
---

### Swift Code Snippet

```
UIView.transition(with: view, duration: 0.5, options: .transitionFlipFromRight, animations: {
  self.flipSideView.isHidden = !self.flipSideView.isHidden
}, completion: nil)
```