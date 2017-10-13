---
layout: post
title:  "Format JSON Pretty Print"
date:   2017-02-08 11:00:00
categories: iOS ObjectiveC Apple
---

Put following code-snippet for formatting a JSON string to pretty print JSON.

```Objective-C
+ (NSString*) formatJSONPretty:(NSData *)data {
    id obj = [NSJSONSerialization JSONObjectWithData:data options:NSJSONReadingAllowFragments error:nil];
    if (obj) {
        NSData* d = [NSJSONSerialization dataWithJSONObject:obj options:NSJSONWritingPrettyPrinted error:nil];
        return [[NSString alloc] initWithData:d encoding:NSUTF8StringEncoding];
    } else {
        return nil;
    }
}
```
