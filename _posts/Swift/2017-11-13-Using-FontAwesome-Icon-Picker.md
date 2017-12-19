---
layout: post
title:  "Using FontAwesome Icon Picker in swift for iOS Apps - SKFontAwesomeIconPickerView"
date:   2017-11-13 10:00:00
categories: Illustration
tags: Font Awesome Icon Picker View Custom 
comments: true
logo: flag
---

# [SKFontAwesomeIconPickerView](https://github.com/sag333ar/SKFontAwesomeIconPickerView)

> An icon picker view which will show list of icons from Font Awesome.

## Demo GIF

![Demo](https://raw.githubusercontent.com/sag333ar/SKFontAwesomeIconPickerView/master/ReadmeAssets/GifDemo.gif)

With the help of Icon Picker View, Icon picker funcationality can be achieved easily.

## Features

- [x] Customizable Icon Color
- [x] Customizable Icon Border Color
- [x] Customizable Icon Border Size
- [x] Customizable Icon Border corner radius
- [x] Customizable Icon Background color
- [x] Customizable Selected Icon Color
- [x] Customizable Selected Icon Border Color
- [x] Customizable Selected Icon Border Size
- [x] Customizable Selected Icon Border corner radius
- [x] Customizable Selected Icon Background color

## Requirements

- iOS 9.0+
- Xcode 9

## Installation

#### CocoaPods
You can use [CocoaPods](http://cocoapods.org/) to install `SKFontAwesomeIconPickerView` by adding it to your `Podfile`:

```ruby
platform :ios, '9.0'
use_frameworks!
pod 'SKFontAwesomeIconPickerView', :git => 'https://github.com/sag333ar/SKFontAwesomeIconPickerView.git', :branch => 'master'
```

To get the full benefits import `SKRadioButton` wherever you import UIKit

``` swift
import UIKit
import SKFontAwesomeIconPickerView
```

## Usage example

***Step 1:*** Download `FontAwesome` from [here](https://github.com/sag333ar/SKFontAwesomeIconPickerView/raw/master/fontawesome-webfont.ttf) or [here](http://fontawesome.io/)

***Step 2:*** Drag & drop font into your Xcode project.

***Step 3:*** Open `Info.plist` and add an entry as indicated below.

![AddFont.png](https://raw.githubusercontent.com/sag333ar/SKFontAwesomeIconPickerView/master/ReadmeAssets/AddFont.png)

***Step 4:*** Open your project's Storyboard. Drag & drop a view. Select it & change Class name to `SKFontAwesomePickerView` as indicated below from Identity Inspector.

![CustomClass.png](https://raw.githubusercontent.com/sag333ar/SKFontAwesomeIconPickerView/master/ReadmeAssets/CustomClass.png)

***Step 5:*** Change your view controller's code as indicated below. Also apply necessary connections to Storyboard.

```swift
import UIKit
import SKFontAwesomeIconPickerView

class ViewController: UIViewController {

  @IBOutlet var iconPicker: SKFontAwesomePickerView!
  @IBOutlet var label: UILabel!
  
  override func viewDidLoad() {
    super.viewDidLoad()
    iconPicker.didSelectClosure = { icon in
      DispatchQueue.main.async {
        self.label.text = icon
      }
    }
  }

}
```

Hope that helps.

If it does not, download sample project from [here](https://raw.githubusercontent.com/sag333ar/SKFontAwesomeIconPickerView/master/ReadmeAssets/SamplePickerView.zip) for more reference.

