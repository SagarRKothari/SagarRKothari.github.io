---
layout: post
title:  "Using Localization Tables for supporting internationalization"
date:   2017-10-29 10:00:00
categories: CodeSnippet
tags: internationalization Localization Swift
---

#### Step 1.

Swift Code Snippet

```swift
let helloWorld = NSLocalizedString("KeyForHelloWorld", // Key of the value
	tableName: "LoginModule", // value to be stored in a table
	bundle: Bundle.main, // using main bundle
	value: "Hello World!", // Default value to be assigned to the key
	comment: "LoginModule - Hello World! This comment is useful for translator.") 
	// comment to provide help to translator
```

----

#### Step 2.

Go to terminal & run following command.

```
xcrun extractLocStrings *.swift
```

Above command will generate multiple strings file based on the different tables you've specified in code.

----

#### Step 3.

Drag & drop those strings file in your project.

----

#### Step 4.

Select one of the strings file, open file inspector & Click on `localize` button to enable localization.

![LocalizationDemo]({{ "/assets/2017-11-01/Localization.png" | absolute_url }})