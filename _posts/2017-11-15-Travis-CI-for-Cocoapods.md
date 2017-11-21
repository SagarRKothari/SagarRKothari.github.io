---
layout: post
title:  "Using Travis-CI for your components - Cocoapods"
date:   2017-11-15 10:00:00
categories: Illustration
tags: TravisCI Continuous Integration CI
comments: true
logo: cogs
---

[Source Of Travis Config](https://github.com/sag333ar/SKRadioButton/blob/master/.travis.yml)

* ***Language:*** Define which `language` to use. Here, we've used `swift`.
* ***osx_image:*** Define which `osx_image` to use. Here, we've used `Xcode9`.
* ***branches:*** Define which `branches` of repository to run CI. Here, we've specified only `master` to run CI.
* ***env:*** Define environment. We've set it to `UTF-8`.
* ***script:*** Define scripts to be executed.

If  pipefail  is  enabled,  the  pipeline's return status is the value of the last (rightmost) command to exit with a non-zero status, or zero if all commands exit successfully.

Here, we're enabling `pipefail` flag by providing following script.

```
set -o pipefail
```

Here, we're building xcode project with `xcodebuild` command.
Please make sure to replace your project's name & scheme name before executing.

```
xcodebuild -project SKRadioButton.xcodeproj -scheme SKRadioButton -sdk iphonesimulator ONLY_ACTIVE_ARCH=NO | xcpretty -c
```


```yml
language: swift
osx_image: xcode9

branches:
 only:
 - master

env:
 - LC_CTYPE=en_US.UTF-8 LANG=en_US.UTF-8

script:
  - set -o pipefail
  - xcodebuild -project SKRadioButton.xcodeproj -scheme SKRadioButton -sdk iphonesimulator ONLY_ACTIVE_ARCH=NO | xcpretty -c
```
