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

### Controllers

* Adds models and behaviors to a section of your page
* 2 flavors
* Just plain ole functions

How to create a controller: ```ng-controller```

### Models

How to create a model: ```$scope``` or ```this```

Behavior = functions

Should be thin(ish)