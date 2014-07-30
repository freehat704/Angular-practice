AngularJS
=========
Super compressed lecture on Angular
-----------------------------------

### Welcome to CampNG!

Note: We were using JSBin to run our angular stuff. Include this in the HTML:

```html
<!DOCTYPE html>
<html ng-app>
<head>
	<meta name="description" content="Camp NG Example 0" />
	<script src="http://code.jquery.com/jquery.min.js"></script>
	<link href="http://getbootstrap.com/2.3.2/assets/css/bootstrap.css" rel="stylesheet" type="text/css" />
	<link href="http://getbootstrap.com/2.3.2/assets/css/bootstrap-responsive.css" rel="stylesheet" type="text/css" />
	<script src="http://getbootstrap.com/2.3.2/assets/js/bootstrap.js"></script>
	<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.2.12/angular.min.js"></script>
	<meta charset=utf-8 />
	<title>JS Bin</title>
</head>
```

### The Old Way

Hey, we used to have everything heavy on the server side. On the client, we only have interactivity.

AJAX mixes this up, and web devopment application changes the achitecture of the client and server.

### The New Way

Client has more things now (MVC). 

Controller is smaller on server side. Sending mainly RESTful JSON back and forth between server and client.

### Angular Zen

Angular is 2nd gen client-side framework. 

Angular Traits

* Simplicity (JS Objects)
* Decoupling (objects doing one things well)
* Binding (bound attributes, very powerful)
* Dependency Injection

> An injection is the passing of a dependency (a service) to a dependent object (a client). The service is made part of the client's state. Passing the service to the client, rather than allowing a client to build or find the service, is the fundamental requirement of the pattern.

[Wikipedia Source](http://en.wikipedia.org/wiki/Dependency_injection)

### Testing

Unit and Functional Testing

### Directives

Founder thought of Angular as HTML complier
Building blocks of Angular

### Angular expressions

Automatically binding

Can be nested

Looks like this: ```{{ stuff }}```

```html
<html ng-app>
```

```html
{{Hello, World!}}
```

### Controllers

* Adds models and behaviors to a section of your page
* 2 flavors
* Just plain ole functions

How to create a controller: ```ng-controller```

```html
<body ng-controller="GreeterCtrl">
  {{ greetee }}
</body>
```

```javascript
function GreeterCtrl($scope) {
  $scope.greetee = "Hi There CampNG!";
}
```

### Models

How to create a model: ```$scope``` or ```this```

* Behavior = functions
* Should be thin(ish)

#### ng-model

* establish a two-way binding between model and view
* Changes from either side are immediately reflected

```html
<body ng-controller="RepeatCtrl">
  <ul>
    <li ng-repeat="fruit in fruits">{{fruit}}</li>
  </ul>
  
  My particulars
  <ul>
    <li ng-repeat="(key, value) in details">{{key}} is {{value}}</li>
    <input ng-model="fruits[0]" />
  </ul>
</body>
```

```javascript
function RepeatCtrl($scope) {
  $scope.fruits = ["Bananas", "Canteloupe", "Cherries", "Strawberries", "Tomatoes"];
  $scope.details = { name: "Chris", age: 41, title: "Occupant" };
}
```

### Loops

Create a scope within a scope: ```ng-repeat = "item in items"```

```html
<body ng-controller="RepeatCtrl">
  <ul>
    <li ng-repeat="fruit in fruits">{{fruit}}</li>
  </ul>
  
  My particulars
  <ul>
    <li ng-repeat="(key, value) in details">{{key}} is {{value}}</li>
  </ul>
</body>
```

```javascript
function RepeatCtrl($scope) {
  $scope.fruits = ["Bananas", "Canteloupe", "Cherries", "Strawberries", "Tomatoes"];
  $scope.details = { name: "Chris", age: 41, title: "Occupant" };
}
```

#### My lab example

```html
<body ng-controller="RepeatCtrl">
  <ul>
    <li ng-repeat="student in students">{{student.name}} is {{student.age}} years old</li>
  </ul>
</body>
```

```javascript
function RepeatCtrl($scope) {
  $scope.sally = { name: "Sally", age: 41, title: "Occupant" };
  $scope.george = { name: "George", age: 30, title: "Occupant" };
  $scope.kim = { name: "Kim", age: 20, title: "Occupant" };
  $scope.students = [$scope.sally, $scope.george, $scope.kim];
}
```

### Track By Expression

> Occurs if there are duplicate keys in an ngRepeat expression. Duplicate keys are banned because AngularJS uses keys to associate DOM nodes with items.

> By default, collections are keyed by reference which is desirable for most common models but can be problematic for primitive types that are interned (share references).

> For example the issue can be triggered by this invalid code:

```html
<div ng-repeat="value in [4, 4]"></div>
```

> To resolve this error either ensure that the items in the collection have unique identity or use the track by syntax to specify how to track the association between models and DOM.

> To resolve the example above can be resolved by using track by $index, which will cause the items to be keyed by their position in the array instead of their value:

```html
<div ng-repeat="value in [4, 4] track by $index"></div>
```

[Source](https://docs.angularjs.org/error/ngRepeat/dupes)

### Binding on click

Check out: ```ng-click```

```html
<body ng-controller="CalculatorCtrl">
  <div>
  <input ng-model="addend" /> + <input ng-model="addend2" /> = {{sum}}
  </div>
  <input type="button" value="Add!" ng-click="add(addend,addend2)" />
</body>
```

```javascript
function CalculatorCtrl($scope) {
  $scope.add = function(addend1, addend2) {
    $scope.sum = addend + addend2;
  };
}
```

Does not do type conversion for us.

```javascript
function CalculatorCtrl($scope) {
  $scope.add = function(addend, addend2) {
    $scope.sum = Number(addend) + Number(addend2);
  };
}
```

Another way of doing it:

```javascript
function CalculatorCtrl($scope) {
  $scope.add = function() {
    $scope.sum = Number($scope.addend) + Number($scope.addend2);
  };
}
```

Changing the students field with a click:

```html
<body ng-controller="StudentCtrl">
  <ul>
    <li ng-repeat="student in students" ng-click="editStudent(student)">{{student.name}} is {{student.age}}</li>
  </ul>
  <input name="name" ng-model="selectedStudent.name" placeholder="Select name"/><br/>
  
  <input name="age" ng-model="selectedStudent.age" placeholder="Select age"/><br/>
  
</body>
```

```javascript
function StudentCtrl($scope) {
  $scope.students = [{name: "Joe", age: 23}, {name: "Chris", age: 41}];
  $scope.editStudent = function(student) {
    $scope.selectedStudent = student;
  };
}
```
