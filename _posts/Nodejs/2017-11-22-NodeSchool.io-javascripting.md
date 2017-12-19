---
layout: post
title:  "NodeSchool.io javascripting solutions"
date:   2017-11-22 10:00:00
categories: nodejs
tags: nodejs js javascripting javascript
comments: true
logo: coffee
---

If you're a beginner & learning Node.js, you should try to start learning from [nodeschool.io](https://nodeschool.io/)
I also did the same & I have added solutions for [`javascripting` ](https://github.com/workshopper/javascripting)

* Learn the basics of JavaScript. No previous programming experience required.
* Learn JavaScript by adventuring around in the terminal.
* Looking for more interactive tutorials like this? Go to [nodeschool.io](https://nodeschool.io/)

### introduction.js

```javascript
console.log('hello');
```

### variables.js

```javascript
var example = 'some string';
console.log(example);
```

### strings.js

```javascript
var someString = 'this is a string';
console.log(someString);
```

### string-length.js

```javascript
var example = 'example string';
console.log(example.length);
```

### revising-strings.js

```javascript
var pizza = 'pizza is alright';
pizza = pizza.replace('alright', 'wonderful');
console.log(pizza);
```

### numbers.js

```javascript
var example = 123456789;
console.log(example);
```

### rounding-numbers.js

```javascript
var roundUp = 1.5;
roundUp = Math.round(roundUp);
console.log(roundUp);
```

### number-to-string.js

```javascript
var n = 128;
console.log(n.toString());
```

### if-statement.js

```javascript
var fruit = 'orange';
if (fruit.length > 5) {
	console.log("The fruit name has more than five characters.");
} else {
	console.log("The fruit name has five characters or less.");
}
```

### for-loop.js

```javascript
var total = 0;
var limit = 10;
for (var i = 0; i < limit; i++) {
	total += i;
}
console.log(total);
```

### arrays.js

```javascript
var pizzaToppings = ["tomato sauce", "cheese", "pepperoni"];
console.log(pizzaToppings);
```

### array-filtering.js

```javascript
var numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
var filtered = numbers.filter(function (number) {
	return number % 2 === 0;
})
console.log(filtered);
```

### accessing-array-values.js

```javascript
var food = ['apple', 'pizza', 'pear'];
console.log(food[1]);
```

### looping-through-arrays.js

```javascript
var pets = ['cat', 'dog', 'rat'];
for (var i = 0; i < pets.length; i++) {
	pets[i] = pets[i] + 's';
}
console.log(pets);
```

### objects.js

```javascript
var pizza = {  
	toppings: ['cheese', 'sauce', 'pepperoni'],  
	crust: 'deep dish',  
	serves: 2  
};
console.log(pizza);
```

### object-properties.js

```javascript
var food = {  
	types: 'only pizza';
};
console.log(food.types);
```

### functions.js

```javascript
function eat(food) {
	return food + ' tasted really good.';
}
console.log(eat('bananas'));
```

### function-arguments.js

```javascript
function math(one, two, three) {
	return two * three + one;
}
console.log(math(53,61,67));
```

### scope.js

```javascript
var a = 1, b = 2, c = 3;  

(function firstFunction(){  
 var b = 5, c = 6;  

 (function secondFunction(){  
     var b = 8;  
     console.log("a: "+a+", b: "+b+", c: "+c);
     (function thirdFunction(){  
         var a = 7, c = 9;  

         (function fourthFunction(){  
             var a = 1, c = 8;  

         })();  
     })();  
 })();  
})(); 
```
