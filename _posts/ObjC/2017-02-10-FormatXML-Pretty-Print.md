---
layout: post
title:  "Format XML Pretty Print"
date:   2017-02-10 09:00:00
categories: CodeSnippet
tags: XML Format String
comments: true
logo: check-circle
---

Put following code snippet for XML Pretty Print

```objc
#import <libxml/tree.h>

+ (NSString *)prettyPrintXML:(NSString *)rawXML {
    const char *utf8Str = [rawXML UTF8String];
    xmlDocPtr doc = xmlReadMemory(utf8Str, (int)strlen(utf8Str), NULL, NULL, XML_PARSE_NOCDATA | XML_PARSE_NOBLANKS);
    xmlNodePtr root = xmlDocGetRootElement(doc);
    xmlNodePtr xmlNode = xmlCopyNode(root, 1);
    xmlFreeDoc(doc);

    NSString *str = nil;

    xmlBufferPtr buff = xmlBufferCreate();
    doc = NULL;
    int level = 0;
    int format = 1;

    int result = xmlNodeDump(buff, doc, xmlNode, level, format);

    if (result > -1) {
        str = [[NSString alloc] initWithBytes:(xmlBufferContent(buff))
                                       length:(NSUInteger)(xmlBufferLength(buff))
                                     encoding:NSUTF8StringEncoding];
    }
    xmlBufferFree(buff);

    NSCharacterSet *ws = [NSCharacterSet whitespaceAndNewlineCharacterSet];
    NSString *trimmed = [str stringByTrimmingCharactersInSet:ws];
    return trimmed;
}
```
