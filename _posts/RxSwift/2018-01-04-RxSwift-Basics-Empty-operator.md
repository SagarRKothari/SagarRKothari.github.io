---
layout: post
title:  "RxSwift Basics - Empty Operator"
date:   2018-01-04 11:00:00
categories: CodeSnippet
comments: true
tags: Reactive ReactiveX Swift RxSwift ReactiveSwift FRP Functional
logo: flash
---

In this page, we'll discuss about empty operator.

Let's start with sample code.

```swift
// 1.
let bag = DisposeBag()

// 2.
let observable = Observable<Void>.empty()

// 3.
observable.subscribe(onNext: { element in
    print(element)
}, onCompleted: {
    print("Completed")
}).disposed(by: bag)
```

- Here, we've created a dispose bag. [We've discussed about this earlier.](http://sagarrkothari.com/2018/01/02/Commonly-used-git-commands/)
- We've created observable of empty type.
- Observer is subsribing to empty-typed-observable.
- We're disposing observer.

Let's take one real-life example.

- Professor gets call while giving lecture.
- He/she goes to corner of the class
- He/she speaks silently (doesn't emit anything).
- Once done, he/she is back and says I'm done with my call.

Let's transform & add little jargons of Reactive programming.

- Professor - observable - takes the call. Students-observers are waiting for his/her call-completion.
- Professor - completes his/her call. Students-observers gets notified - via - onComplete.
- Professor - observable - doesn't emit any kind of data.
- Now, time to check the code. See the code written below & try to map above example.

```swift
let bag = DisposeBag()

let observable = Observable<Void>.empty() // Professor who is on call

observable.subscribe(onNext: { element in
print(element) // professor won't transfer data to students

}, onCompleted: {

print("Completed") // professor will inform students once call is complete.

}).disposed(by: bag)
```

Note: I knew, you being eagle-eyed reader, cant' resist to ask why have I used word operator for empty.

You may continue with another question, Isn't it a function? Yes, You're right.
It is a function, but in Reactive programming, It's known as an operator.

So far, we've covered following Reactive programming operators.

- `.just(one)` - creates an observable with just one element
- `.of(one, two, three, many)` - creates an observable with multiple elements
- `.empty()` - creates an observable which just emits completed & not next.

---
