---
layout: post
title:  "Using Coredata in Xcode 9 supporting iOS 10 and above"
date:   2017-11-12 10:00:00
categories: Illustration
tags: CoreData SQLite XCode9 iOS10 Store Storage Offline CRUD operation Database
comments: true
logo: database
---

In this post, I've explained about using core data in Xcode 9 which supports iOS 10 and above.

***Step 1:*** Create a project with core data (as illustrated below).

![Step 1]({{"/assets/2017-11-12/step1.png" | absolute_url}})

***Step 2:*** Make sure that under `AppDelegate.swift` file, you've following piece of code.
Usually, you'll find that by default under same file if you've followed step-1 correctly.

```swift

import CoreData
  
  lazy var persistentContainer: NSPersistentContainer = {
  	// Here it would be your project CoreData model name instead 'SampleData'
    let container = NSPersistentContainer(name: "SampleData")
    container.loadPersistentStores(completionHandler: { (storeDescription, error) in
      if let error = error as NSError? {
        fatalError("Unresolved error \(error), \(error.userInfo)")
      }
    })
    return container
  }()
  
  // MARK: - Core Data Saving support
  
  func saveContext () {
    let context = persistentContainer.viewContext
    if context.hasChanges {
      do {
        try context.save()
      } catch {
        let nserror = error as NSError
        fatalError("Unresolved error \(nserror), \(nserror.userInfo)")
      }
    }
  }

```

***Step 3:*** Add following two lines, before class `AppDelegate` declaration.

```swift
import UIKit
import CoreData

let appDel = (UIApplication.shared.delegate as? AppDelegate)!
let context = appDel.persistentContainer.viewContext

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
```

***Step 4:*** Add necessary entities, relations under `yourProject.xcdatamodelId` file. My file is as follows.

![Step 4]({{"/assets/2017-11-12/step4.png" | absolute_url}})

Here, for this article, we'll be using just one entity called `Office` which will have `name` and `sortIndex` as attributes.

***Step 5:*** Following is the piece of code which can be used for CRUD operations.

```swift
extension ViewController {

  func save() {
    do {
      // if you've followed step 3 correctly, you'll have access to context variable.
      try context.save()
    } catch {
      
    }
  }

  func addData(_ name: String) {
    let object = Office(context: context)
    object.name = name
    object.sortIndex = Int64(offices.count)
    save()
  }

  func delete(_ office: Office) {
    context.delete(office)
    save()
  }

  func update(_ office: Office, name: String) {
    office.name = name
    save()
  }

  func getOffices() -> [Office] {
    do {
      var offices = (try context.fetch(Office.fetchRequest()) as? [Office])!
      offices.sort(by: { $0.sortIndex < $1.sortIndex })
      return offices
    } catch {
      return []
    }
  }

}
```

Hope that helps. Cheers!

---