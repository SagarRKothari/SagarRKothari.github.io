---
layout: post
title:  "Implementing Reachability with Singleton"
date:   2017-02-14 10:00:00
categories: Swift
tags: Reachability WiFi
---

#### Download Reachability class

[Click to download]({{"assets/2017-02-14-Implementing-Reachability/Reachability.swift" | absolute_url }})

#### Rechability Checker

```swift
import Foundation

public class ReachabilityChkr: NSObject {
    
    let reachability = Reachability()!
    
    override init() {
        super.init()
        reachability.whenReachable = { reachability in
            performUIUpdatesOnMain({
                if reachability.isReachableViaWiFi {
                    print("Reachable via WiFi")
                } else {
                    print("Reachable via Cellular")
                }
            })
        }

        reachability.whenUnreachable = { reachability in
            performUIUpdatesOnMain({
                print("Not reachable")
            })
        }

        do {
            try reachability.startNotifier()
        } catch {
            print("Unable to start notifier")
        }
    }

    public class var shared: Reachability {
        get {
            struct Single {
                static var shared = ReachabilityChkr()
            }
            return Single.shared.reachability
        }
    }

}
```

#### Use above class

```
if ReachabilityChkr.shared.isReachableViaWiFi == true || ReachabilityChkr.shared.isReachableViaWWAN == true {
    print("Connected to Internet")    
} else {
    print("=== NOT Connected to Internet ===")
}
```

_**Categories:**_ {{ page.categories | array_to_sentence_string }} \| _**Tags:**_ {{ page.tags | array_to_sentence_string }}