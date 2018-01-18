---
layout: post
title:  "RxSwift Basics - understanding observables and observers"
date:   2018-01-01 11:00:00
categories: CodeSnippet
comments: true
tags: Reactive ReactiveX Swift RxSwift ReactiveSwift FRP Functional
logo: flash
---

Before we jump into basic fundaments of Reactive Programming, I woule like to share an real-life example here.

Let's assume, in a classroom, Professor is giving lecture. Students are listening/observing/paying attention to Professor's explaination. Bell peals as lecture duration is complete. Professor ends his/her lecture. Class is dismissed.

Here, I'll try to same things by injecting few words/jargons of Reactive programming, in above example. 

- Professor is observable. 
- Students are observers. 
- Professor is emmiting words/knowledge
- Students are receiving. 
- On lecture completion, class is dismissed.

Now, I'll say the same set of things in complete Reactive terms.

- Observable - to which observers/subscribers can listen/receive events.
- Observers/Subscribers - those who are listening to observables.
- next - Next is an event in which observers get data from observables at periodic times. For example, during data download, observables can emit chunks of data, using next, to observers.
- onComplete - An event, which is triggered by observables once they are done emitting. 
- dispose - This is not event. To avoid memory leaks, all subscribers/observables are needed to be disposed. 

Let's understand things which I've just said by an example.

```swift
import RxSwift

print("--- Example of: First RxSwift Code ---")
// 1.
let name = "Sagar"
let fathersName = "Rajeshbhai"
let surname = "Kothari"

// 2.
let observable: Observable<String> = Observable<String>.of(name, fathersName, surname)

// 3. 
let observer = observable.subscribe { event in
   print(event)
}

// 4.
let bag = DisposeBag()

// 5.
observer.disposed(by: bag)
```

1. I've collected data here which needs to be `emitted` by `observable`
2. I've created an `observable` with given data set with `of` operator. Here, I've created a string typed `observable`. It can be of any type.
3. Here, I've created an `observer`, which `subscribes` to events of `observable`. On receving an event, it will print the event received.
4. I've created a `DisposeBag` which will be used to dispose `observers`.
5. This line of code will `dispose` the observer.

Output of above code looks as follows.

```
--- Example of: First RxSwift Code ---
next(Sagar)
next(Rajeshbhai)
next(Kothari)
completed
```

You being an eagle-eyed reader, might have spotted `completed` at the end of console log. Yes, you're right, `observable` also emits `completed` event.

Let's refactor above code with some RxSwift features.

```swift
import RxSwift

let name = "Sagar"
let fathersName = "Rajeshbhai"
let surname = "Kothari"
print("--- Example of: Second RxSwift Code ---")
let observable: Observable<String> = Observable<String>.of(name, fathersName, surname)

let observer = observable.subscribe(onNext: { string in
   print(string)
}, onCompleted: {
   print("Completed")
})

let bag = DisposeBag()
observer.disposed(by: bag)
```

And output is as follows.

```
--- Example of: Second RxSwift Code ---
Sagar
Rajeshbhai
Kothari
Completed
```