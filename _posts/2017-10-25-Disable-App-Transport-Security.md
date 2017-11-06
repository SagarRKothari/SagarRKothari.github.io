---
layout: post
title:  "Disabling App Transport Security"
date:   2017-10-25 10:00:00
categories: CodeSnippet
tags: Application Transport Security
---

### Step 1.

Open your project.

### Step 2.

Open `Info.plist` as source code (right click on `Info.plist`).

### Step 3.

Before (look for end of file)

```xml
</dict>
</plist>
```

Insert following

```xml
<code class="xml">
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
</dict>
</code>
```