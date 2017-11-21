---
layout: post
title:  "Sorting Elements to Support re-arrangement with core data having sortIndex as attribute"
date:   2017-11-14 10:00:00
categories: CodeSnippet
tags: Sort Rearrange Arrange Index SortIndex CoreData
comments: true
logo: compress
---

![Demo]({{"/assets/2017-11-14/GifDemo.gif" | absolute_url}})

In this article, I've added logic for sorting elements and storing the sort index in core data.

```swift
import CoreData

let appDel = (UIApplication.shared.delegate as? AppDelegate)!
let context = appDel.persistentContainer.viewContext

// code which whould be part of table-view-controller

  func tableView(_ tableView: UITableView, moveRowAt fromIndexPath: IndexPath, to: IndexPath) {
    offices[fromIndexPath.row].sortIndex = Int64(to.row)
    var startIndex = 0
    var endIndex = offices.count-1
    if fromIndexPath.row > to.row {
      startIndex = to.row
      endIndex = fromIndexPath.row
    } else {
      startIndex = fromIndexPath.row
      endIndex = to.row
    }
    for i in startIndex..<endIndex {
      offices[i].sortIndex = Int64(i)
    }
    save()
  }

  func save() {
    do {
      try context.save()
    } catch {
      
    }
  }

```

Data Structure is as shown in below image.

![Data Structure]({{"/assets/2017-11-12/step4.png" | absolute_url}})