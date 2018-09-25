---
layout: post
title:  "Android Basics - How to show back button on an Activity?"
date:   2018-09-23 10:15:00
categories: CodeSnippet
tags: Android Kotlin Activity
comments: true
logo: android
---

You should have at-least two activities.

- Parent activity from which another activity is getting displayed.
- Another activity which is shown from parent activity.

#### Example:

- Login activity = Parent activity = `LoginActivity`
- Forgot Password activity = Child activity = `ForgotPasswordActivity`

#### How to set up?

1. Open `AndroidManifest.xml`
2. Locate child activity, in my case it is `ForgotPasswordActivity` & replace it as follows.

```xml
<activity android:name=".LoginActivity" />

<activity android:name=".ForgotPasswordActivity">
    <meta-data
        android:name="android.support.PARENT_ACTIVITY"
        android:value=".LoginActivity" />
</activity>
```

![Demo Output for Android]({{"assets/2018-09-24/backButton.png" | absolute_url}})
