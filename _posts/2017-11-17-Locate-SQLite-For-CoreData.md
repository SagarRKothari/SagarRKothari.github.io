---
layout: post
title:  "Locate SQLite file for Core Data application"
date:   2017-11-17 10:00:00
categories: CodeSnippet
tags: CoreData Database SQLite File Locate
comments: true
logo: database
---

If you're using coredata in your application, sometimes you might need to open database & check actuall values. I prefer to use [DB Browser For SQLite]({{ "2017/11/16/SQLite-Browser-For-mac/" | absolute_url}}).

### How to locate SQLite file?

Put following piece of code under `AppDelegate` - `didFinishLaunching` method.

```swift
let path = NSSearchPathForDirectoriesInDomains(.applicationSupportDirectory, .userDomainMask, true)
print("\(path)")
```

Above code will simply print the path of `Library-ApplicationSupport` of your application, which should look like following.


```
["/Users/sagar/Library/Developer/CoreSimulator/Devices/4A09A062-C286-4B9A-A60C-4D664E7CF451/data/Containers/Data/Application/48F17B59-8876-4FDF-AEF9-BDDD533079E7/Library/Application Support"]
```

As you can see, there are two identifiers in the folder-structure-path. One is identifier of the Simulator & the other one is of your-application.

***Step 1.*** Copy the message from console, after running the application on iOS Simulator.

***Step 2.*** Open finder & press `CMD+G` to open `Go To Folder` as indicated below & paste the copied path.

![Step2]({{"/assets/2017-11-17/step1.png" | absolute_url}})

***Step 3.*** You should be able to locate `SQLite` file now. In my case it is `SampleData.sqlite`

![Step3]({{"/assets/2017-11-17/step2.png" | absolute_url}})