---
layout: post
title:  "Generate with URL Components like host, path, params"
date:   2017-02-13 10:00:00
categories: CodeSnippet
tags: URL Components Generator
comments: true
logo: firefox
---

Code snippet for generating URL using scheme, host, path, parameters and path extension

```swift
func formURL(scheme: String, 
               host: String,
               path: String,
             params: [String:String]?, 
      pathExtension: String? = nil) -> URL {

        let components = NSURLComponents()

        // 1. http or https
        components.scheme = scheme 

        // 2. host (eg. api.google.com)
        components.host = host

        // 3. path (eg. /index)
        // and 4. path extension (eg. php)
        components.path = path + (pathExtension ?? "")

        // 5. query parameters
        components.queryItems = [NSURLQueryItem]() as [URLQueryItem]?

        // for-loop to set 
        if  params != nil {
            for (key, value) in (params)! {
                let queryItem = NSURLQueryItem(name: key, value: "\(value)")
                components.queryItems!.append(queryItem as URLQueryItem)
            }
        }
        print("Generated URL is \(components.url!)")
        return components.url!
}
```

