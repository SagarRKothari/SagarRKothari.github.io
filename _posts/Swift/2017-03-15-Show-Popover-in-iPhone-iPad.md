---
layout: post
title:  "Show Popover in iPhone or iPad without any third party library"
date:   2017-03-15 10:00:00
categories: Illustration
tags: UIKit Popover iPad iPhone
comments: true
logo: object-ungroup
---

## Show Popover in iPhone-iPad

In this post, I'll explain how to show pop-over on iPhone/iPad without using any third party library.

### Step 1.

Open your project & make sure you've one class from where you would like to show the pop-over and another class for the pop-over.

![Step 1]({{ "/assets/2017-03-15/Classes.png" | absolute_url }})

### Step 2.

Open Storyboard & add a new view controller for pop-over & resize as per your need. Make sure you also apply the class name to view-controller.

![Step 2]({{ "/assets/2017-03-15/HowToShowPopOver-1.gif" | absolute_url }})

### Step 3.

In your view-controller, add bar-button from where you can drag & drop segue to pop-over-controller.

**Make sure you give the name to the segue.**

![Step 3]({{ "/assets/2017-03-15/HowToShowPopOver-2.gif" | absolute_url }})

### Step 4.

In your view-controller, you make sure to extend `UIPopoverPresentationControllerDelegate`

### Step 5.

Put following delegate method in your-view-controller.


```swift
func adaptivePresentationStyle(for controller: UIPresentationController) 
    -> UIModalPresentationStyle {
    return UIModalPresentationStyle.none
}
```

### Step 6.

Put following method in your-view-controller & identify segue.

```swift
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
    if segue.identifier == "from_home_to_popover" {
        if let vctr = segue.destination as? MyPopOverViewController {
            vctr.modalPresentationStyle = .popover
            vctr.popoverPresentationController?.delegate = self
            vctr.popoverPresentationController?.sourceView = self.view
            vctr.popoverPresentationController?.sourceRect = self.btn.frame
        }
    }
}
```

### Step 7.

Put following code in your pop-over-controller under `viewDidLoad`.

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    self.preferredContentSize = CGSize(width: 300, height: 300)
}
```

### Step 8.

From some action, when you wish to dismiss pop-over, under your pop-over-controller put following code.

```swift
@IBAction func btnDoneTapped(btn: UIButton) {
    self.dismissViewControllerAnimated(true, completion: nil)
}
```

Example output is as follows.

![Output]({{ "/assets/2017-03-15/HowToShowPopOver-3.gif" | absolute_url }})


## Download Source code

[Download]({{ "/assets/2017-03-15/ShowPopover.zip" | absolute_url }})
