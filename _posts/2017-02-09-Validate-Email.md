---
layout: post
title:  "Validate Email"
date:   2017-02-09 10:00:00
categories: Objective-C
tags: Email Validation String Regex Predicate
---

Code snippet to validate an email

```Objective-C
- (BOOL) validateEmail: (NSString *) candidate {
    NSString *emailRegex = @"[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,4}";
    NSPredicate *emailTest = [NSPredicate predicateWithFormat:@"SELF MATCHES %@", emailRegex];
    return [emailTest evaluateWithObject:candidate];
}
```

_**Categories:**_ {{ page.categories | array_to_sentence_string }} \| _**Tags:**_ {{ page.tags | array_to_sentence_string }}
