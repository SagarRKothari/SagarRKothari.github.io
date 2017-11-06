---
layout: post
title:  "Taking Screenshot programmatically"
date:   2017-11-05 10:00:00
categories: CodeSnippet
tags: Swift UIScreen ScreenShot
---

Please find the code snippet as follows for taking screenshot programmatically.

```swift
func screenShotMethod() {
    //Create the UIImage
    UIGraphicsBeginImageContext(view.frame.size)
    view.layer.renderInContext(UIGraphicsGetCurrentContext())
    let image = UIGraphicsGetImageFromCurrentImageContext()
    UIGraphicsEndImageContext()
    //Save it to the camera roll
    UIImageWriteToSavedPhotosAlbum(image, nil, nil, nil)
}
```