---
layout: post
title:  "AngularJS basics from W3School"
date:   2018-10-23 9:00:00
categories: CodeSnippet
tags: AngularJS, HTML, Basics
comments: true
logo: angular
---

#### Example1: `ng-app`, `ng-model`, `ng-bind`

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<div ng-app="">
<p>Name: <input type="text" ng-model="name"></p>
<p ng-bind="name"></p>
</div>
```

#### Example2: `ng-init`, `ng-bind`

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<div 
ng-app="" 
ng-init="firstName='John';developer='Sagar'">

<p>The name is <span ng-bind="firstName"></span></p>
<p>The developer is <span ng-bind="developer"></span></p>

</div>
```

#### Example3: `expressions`

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<div ng-app="">
<p>My first expression: { { 5 + 5 } }</p>
</div>
```

#### Example4: `expressions`, `ng-model`

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<div ng-app="">
<p>Name: <input type="text" ng-model="name"></p>
<p> { { name } } </p>
</div>
```

#### Example5: `ng-app`, `ng-controller`, `expression`

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<div ng-app="myApp" ng-controller="myController">

<table border="1">
<tr>
<td colspan="2">
{ { firstname + " " + lastname } }
</td>
</tr>
<tr>
<td>First name:</td>
<td><input type="text" ng-model="firstname"></td>
</tr>
<tr>
<td>Last name:</td>
<td><input type="text" ng-model="lastname"></td>
</tr>
</table>

<script>
var app = angular.module('myApp', []);
app.controller('myController', function($scope) {
$scope.firstname = "Sagar";
$scope.lastname = "Kothari";
});
</script>
</div>
```

#### Example6: `ng-model`, `ng-init`, `expression`

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<div ng-app="" ng-init="myColor='yellow'">
<input style="background-color:{ { myColor } }" ng-model="myColor">
</div>
```

#### Example7: `ng-model`, `ng-init`, `expression`

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<div ng-app="" ng-init="qty=5;cost=10">
<p> Total cost: { { qty * cost } } </p>
</div>
```
