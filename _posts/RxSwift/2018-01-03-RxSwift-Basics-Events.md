---
layout: post
title:  "RxSwift Basics - Events"
date:   2018-01-03 11:00:00
categories: CodeSnippet
comments: true
tags: Reactive ReactiveX Swift RxSwift ReactiveSwift FRP Functional
logo: flash
---

Let's assume, in a classroom, Professor is giving lecture.

* Students are listening/observing/paying attention to Professor's explanation.
* Bell peals as lecture duration is complete.
* Professor ends his/her lecture. Class is dismissed.

Now, let's consider one error scenario here.

* During lecture, Dean calls professor to meat him immediately.

- Professor is observable.
- Students are observers.
- Professor is emitting words/knowledge

Normal scenario

- Students are receiving.
- On lecture completion, class is dismissed.

Error scenario

- Dean call professor. (An error occurred)
- Lecture is over. Class dismissed.
- Now, I'll say the same set of things in complete Reactive terms.

Events

- `onNext` - Students receiving knowledge.
- `onError` - Dean calls professor. (An error occurred).
- `onComplete` - Lecture is over.
- `onDispose` - Class dismissed.

Here is how code looks like.

```swift
let bag = DisposeBag() // 1. Dispose bag

// 2. Lecture data / Objects to be emitted
let one = 1
let two = 2
let three = 3

// 3. Observable/Professor
let observable = Observable<Int>.of(one, two, three)

// 4. Set of events in Reactive format
observable.subscribe(

onNext: { print($0) }, // Student receiving data. Observer printing data on receiving.

onError: { print($0) }, // Dean calls professor. If error occurs, onError gets called.

onCompleted: { print("Complete") }, // This gets called once lecture is complete.

onDisposed: { print("Disposed") } // This gets called when class is dismissed.

).disposed(by: bag)
```
