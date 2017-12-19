---
layout: post
title:  "NodeJS - lodash utility"
date:   2017-11-23 10:00:00
categories: nodejs
tags: nodejs js javascripting javascript lodash
comments: true
logo: coffee
---

Example of [`lodash`](https://lodash.com/docs/4.17.4) module utilities.

```javascript
const _ = require('lodash');
```

Utility Example 1: Example of Unique array filter.

```javascript
console.log(_.uniq([1,2,3,1]));
// it prints [ 1, 2, 3 ]
```

Utility Example 2: Example of Unique array filter.

```javascript
console.log(_.uniq(['Sagar', 'Kothari', 1, 2, 3, 1, 'Sagar']));
// it prints [ 'Sagar', 'Kothari', 1, 2, 3 ]
```

Utility Example 3: Validation 

```javascript
console.log(_.isString(true));
// it prints false
```

Utility Example 4: Validation 

```javascript
console.log(_.isString('Sagar'));
// it prints true
```