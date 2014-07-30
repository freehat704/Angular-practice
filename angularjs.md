AngularJS
=========
Super compressed lecture on Angular
-----------------------------------

### Welcome to CampNG!

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