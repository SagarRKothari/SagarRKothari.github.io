---
layout: post
title:  "Validate Email"
date:   2017-02-09 10:00:00
categories: CodeSnippet
tags: Email Validation String Regex Predicate Swift
comments: true
logo: shield
---

Code snippet to validate an email

```objc
- (BOOL) validateEmail: (NSString *) candidate {
  NSString *emailRegex = @"[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,4}";
  NSPredicate *emailTest = [NSPredicate predicateWithFormat:@"SELF MATCHES %@", emailRegex];
  return [emailTest evaluateWithObject:candidate];
}
```


```swift

  func validateEmail(_ email: String) -> Bool {
    let emailRegEx = "[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,64}"
    let emailTest = NSPredicate(format:"SELF MATCHES %@", emailRegEx)
    return emailTest.evaluate(with: email)
  }

```