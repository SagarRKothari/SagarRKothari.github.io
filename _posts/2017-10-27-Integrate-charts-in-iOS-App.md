---
layout: post
title:  "Integrating Charts in iOS Application"
date:   2017-10-27 10:00:00
categories: Illustration
tags: Charts Library iOS Swift Customization UserInterface
---

### Step 1.

Open your project's Podfile and add following line.

```
pod 'Charts'
```

----

### Step 2.

Open terminal and jump to your project directory.
Run following command.

```
pod install
```

----

### Step 3. 

Open your `viewController.swift` and make sure you import chart library.

```swift
import Charts
```

----

### Step 4.

* Open your storyboard file
* Drag-drop an object of `UIView`.
* Select it
* Go to `Identity Inspector`
* Change class to your chart you want. 

In this article, I'll show using `BarChartView`.

---

### Step 5.

Set up chart on `viewDidLoad`.

```swift
import UIKit
import Charts

class MyViewController: UIViewController {

  // MARK:- IBOutlets
  @IBOutlet weak var barChartView: BarChartView!

  override func viewDidLoad() {
    super.viewDidLoad()
    barChartView.noDataText = "You need to provide data for the chart."
    barChartView.xAxis.labelPosition = .bottom // position of xAxis labels
    barChartView.chartDescription?.text = "Provide chart description here."
  }

}
```

---

### Step 6. 

Make sure you have valid data array.

```swift
// Labels
var months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]

// Values
var soldUnits = [10, 15, 20, 18, 17, 22, 16, 19, 21, 22, 25, 27]

// Colors array if you want to colorize 
var colors = [UIColor.red, UIColor.gray, UIColor.black,
	UIColor.blue, UIColor.brown, UIColor.green,
	UIColor.yellow, UIColor.lightGray, UIColor.magenta,
	UIColor.orange, UIColor.purple, UIColor.darkGray]
```

---

### Step 7. 

Create Chart Data. In this case, we'll be creating bar chart data.

```swift
var dataEntries: [BarChartDataEntry] = []
for i in 0..<soldUnits.count {
  let dataEntry = BarChartDataEntry(x: Double(i), yValues: [Double(soldUnits[i])])
  dataEntries.append(dataEntry)
}
let chartDataSet = BarChartDataSet(values: dataEntries, label: "Sold Units")
let chartColorsData = colors
let chartData = BarChartData(dataSet: chartDataSet)
```

---

### Step 8. 

Create Bar Chart Formatter. This formatter will apply X-Axis values to Chart.
IMPORTANT: If we don't do this, chart will not show anything on X-Axis.

```
import UIKit
import Charts

@objc(BarChartFormatter)
public class BarChartFormatter: NSObject, IAxisValueFormatter {
  var xAxisData: [String] = []
  public func stringForValue(_ value: Double, axis: AxisBase?) -> String {
    return xAxisData[Int(value)]
  }
}
```

### Step 9.

Supply Chart Data to `ChartView`.

```swift
barChartView.data = chartData // From Step 7
let formato = BarChartFormatter() // From Step 8
formato.xAxisData = months 
let xaxis:XAxis = XAxis()
xaxis.valueFormatter = formato
self.barChartView.xAxis.valueFormatter = xaxis.valueFormatter
self.updateData(profitInfo)
```