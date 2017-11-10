---
layout: post
title:  "Using Radio buttons in iOS application Swift - SKRadioButton"
date:   2017-11-10 10:00:00
categories: Illustration
tags: Radio Button
---

## Installation

#### CocoaPods
You can use [CocoaPods](http://cocoapods.org/) to install [`SKRadioButton`](https://github.com/sag333ar/SKRadioButton) by adding it to your `Podfile`:

```ruby
platform :ios, '9.0'
use_frameworks!
pod 'SKRadioButton'
```

To get the full benefits import `SKRadioButton` wherever you import UIKit

``` swift
import UIKit
import SKRadioButton
```

#### Manually

1. Download and drop `SKRadioButton.swift` in your project.  
2. Congratulations!  

## Usage example

***Step 1:*** Open `Storyboard`, Drag and drop a `UIButton` inside your view of `ViewController`.

![Drag & Drop Button](https://raw.githubusercontent.com/sag333ar/SKRadioButton/master/ReadmeAssets/Step1.png)

***Step 2:*** Change the `Class` and `Module` from `Class inspector` for `UIbutton`s which you want to convert to Radio button.

![Change Class](https://raw.githubusercontent.com/sag333ar/SKRadioButton/master/ReadmeAssets/Step2.png)

***Step 3:*** Select your buttons, Change `Type` to `Custom`, remove button `Title` + `Image` + `Background`. Apply Radio buttons customization.

![Change Attributes](https://raw.githubusercontent.com/sag333ar/SKRadioButton/master/ReadmeAssets/Step3-1.png)

![Change Attributes2](https://raw.githubusercontent.com/sag333ar/SKRadioButton/master/ReadmeAssets/Step3-2.png)

***Step 4:*** Place your Radio buttons inside a stack view (recommended) & apply necessary constraints as per your needs.

![Use Stackview](https://raw.githubusercontent.com/sag333ar/SKRadioButton/master/ReadmeAssets/Step4.png)

***Step 5:*** One by one, select your Radio buttons & connect with `Outlet Collection` to your `viewController` as indicated below.

![Outlet Collection](https://raw.githubusercontent.com/sag333ar/SKRadioButton/master/ReadmeAssets/Step5.png)

***Step 6:*** One by one, select your Radio buttons & connect same `Action` to your `viewController`s `IBAction` as indicated below.

![IBAction Connection](https://raw.githubusercontent.com/sag333ar/SKRadioButton/master/ReadmeAssets/Step6.png)

***Step 7:*** Add following piece of code & you're done.


```swift
import UIKit
import SKRadioButton // Step 1. Import SKRadioButton

class ViewController: UIViewController {

  // Step 2. collection of radio buttons
  @IBOutlet var genderRadioButtons: [SKRadioButton]!

  override func viewDidLoad() {
    super.viewDidLoad()
  }

  // Step 3. On tap update 'isSelected' attributes
  @IBAction func genderRadioButtonsTapped(_ sender: SKRadioButton) {
    genderRadioButtons.forEach { (button) in
      button.isSelected = false
    }
    sender.isSelected = true
  }

 }
```

Cheers.