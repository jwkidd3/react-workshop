# Session 2 - Part 2: Scope and Closures

## Prototypes and Inheritance

JavaScript uses **prototypal inheritance**, which means that objects can inherit properties and methods from other objects. In this section, we'll explore how prototypes and inheritance work in JavaScript.

### Object Prototypes

Every object in JavaScript has a prototype, which is another object that it inherits properties and methods from. You can access an object's prototype using the `__proto__` property, like this:

```javascript
const obj = {};
console.log(obj.__proto__); // logs {}

const arr = [];
console.log(arr.__proto__); // logs []
```

In this example, we create an empty object `obj` and an empty array `arr`, and log their prototypes using the `__proto__` property. The empty object's prototype is an empty object `{}`, while the empty array's prototype is an empty array `[]`.

### Prototype Chains

When you try to access a property or method on an object, JavaScript first looks for that property or method on the object itself. If it doesn't find it there, it looks for it on the object's prototype, and so on up the prototype chain until it either finds the property or reaches the end of the chain (which is usually the `Object.prototype`).

Here's an example:

```javascript
const obj = { name: "Alice" };

console.log(obj.hasOwnProperty("name")); // logs true
console.log(obj.hasOwnProperty("toString")); // logs false
console.log(obj.__proto__.hasOwnProperty("toString")); // logs true
console.log(obj.__proto__.__proto__.hasOwnProperty("toString")); // logs true
console.log(obj.__proto__.__proto__.__proto__); // logs null
```

In this example, we create an object `obj` with a `name` property. We then use the `hasOwnProperty` method to check whether `obj` has the `name` property (which it does), and whether it has the `toString` method (which it doesn't). We then log the `hasOwnProperty` method of `obj`'s prototype (`Object.prototype`), and of `Object.prototype`'s prototype (`null`), both of which have the `toString` method.

### Constructor Functions

In addition to creating objects using object literals, you can also use **constructor functions** to create objects with shared properties and methods. A constructor function is a function that is used to create objects.

Here's an example:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name}`);
};

const alice = new Person("Alice", 25);
const bob = new Person("Bob", 30);

alice.sayHello(); // logs "Hello, my name is Alice"
bob.sayHello(); // logs "Hello, my name is Bob"
```

In this example, we define a constructor function `Person` that takes a `name` and an `age` parameter, and sets those values as properties on the new object created by the constructor function using the `this` keyword. We also add a `sayHello` method to the `Person` prototype.

We then create two new `Person` objects using the `new` keyword, passing in the `name` and `age` values for each person. Finally, we call the `sayHello` method on each object to log a greeting to the console.

Constructor functions are a powerful tool in JavaScript for creating objects with shared properties and methods, and for implementing inheritance using the prototype chain.

### Inheritance with Prototypes

One of the most powerful features of prototypes is that they allow you to implement inheritance in JavaScript. Inheritance is the ability of an object to inherit properties and methods from a parent object.

Here's an example:

```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.walk = function() {
  console.log(`${this.name} is walking`);
};

function Bird(name) {
  Animal.call(this, name);
}

Bird.prototype = Object.create(Animal.prototype);
Bird.prototype.constructor = Bird;

Bird.prototype.fly = function() {
  console.log(`${this.name} is flying`);
};

const bird = new Bird("Tweety");

bird.walk(); // logs "Tweety is walking"
bird.fly(); // logs "Tweety is flying"
```

In this example, we define a constructor function `Animal` that sets a `name` property on the object using the `this` keyword, and adds a `walk` method to the `Animal` prototype.

We then define a constructor function `Bird` that calls the `Animal` constructor function using `call`, passing in the `name` parameter and setting `this` to the current object. We then create a new `Bird` prototype using `Object.create` and set its constructor to `Bird`.

Finally, we add a `fly` method to the `Bird` prototype and create a new `Bird` object `bird`. We call the `walk` and `fly` methods on `bird`, which log messages to the console.

In this example, `Bird` inherits from `Animal`, and `Bird.prototype` is a prototype chain that extends from `Bird` to `Animal` to `Object`. By setting `Bird.prototype` to a new object created with `Object.create(Animal.prototype)`, we ensure that any new `Bird` object created will have access to `Animal`'s properties and methods, as well as any properties and methods defined on `Bird.prototype`.

### Classical Inheritance with ES6 Classes

In ES6, JavaScript introduced a new syntax for defining classes, which provides a more familiar syntax for programmers coming from classical object-oriented languages like Java and C++.

Here's an example:

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  walk() {
    console.log(`${this.name} is walking`);
  }
}

class Bird extends Animal {
  fly() {
    console.log(`${this.name} is flying`);
  }
}

const bird = new Bird("Tweety");

bird.walk(); // logs "Tweety is walking"
bird.fly(); // logs "Tweety is flying"
```

In this example, we define a class `Animal` with a constructor that sets a `name` property on the object using the `this` keyword, and a `walk` method.

We then define a class `Bird` that extends `Animal`, using the `extends` keyword. We add a `fly` method to the `Bird` class.

Finally, we create a new `Bird` object `bird` and call the `walk` and `fly` methods on it.

Under the hood, classes in JavaScript are still implemented using prototypes and constructor functions, but the syntax is more familiar to programmers coming from classical object-oriented languages.

## Exercises

1. Create a `Vehicle` constructor function with properties `make` and `model`, and a `start` method that logs "The vehicle is starting".

<details>
  <summary>Answer</summary>
  
```javascript
function Vehicle(make, model) {
  this.make = make;
  this.model = model;
}

Vehicle.prototype.start = function() {
  console.log("The vehicle is starting");
};
```
</details>

2. Create a `Car` constructor function that extends `Vehicle`, with an additional property `numWheels` and a method `drive` that logs "The car is driving".

<details>
  <summary>Answer</summary>

```javascript
function Car(make, model) {
  Vehicle.call(this, make, model);
  this.numWheels = 4;
}

Car.prototype = Object.create(Vehicle.prototype);
Car.prototype.constructor = Car;

Car.prototype.drive = function() {
  console.log("The car is driving");
};
```
</details>

3. Create a `Truck` constructor function that extends `Vehicle`, with an additional property `numWheels` and a method `haul` that logs "The truck is hauling".

<details>
  <summary>Answer</summary>
  
```javascript
function Truck(make, model) {
  Vehicle.call(this, make, model);
  this.numWheels = 6;
}

Truck.prototype = Object.create(Vehicle.prototype);
Truck.prototype.constructor = Truck;

Truck.prototype.haul = function() {
  console.log("The truck is hauling");
};
```
</details>


4. Create a `Plane` constructor function that extends `Vehicle`, with an additional property `numWings` and a method `fly` that logs "The plane is flying".

<details>
  <summary>Answer</summary>
  
```javascript
function Plane(make, model) {
  Vehicle.call(this, make, model);
  this.numWings = 2;
}

Plane.prototype = Object.create(Vehicle.prototype);
Plane.prototype.constructor = Plane;

Plane.prototype.fly = function() {
  console.log("The plane is flying");
};
```
</details>


5. Create instances of each of the `Car`, `Truck`, and `Plane` constructors, and call their respective methods.

<details>
  <summary>Answer</summary>

```javascript
const car = new Car("Toyota", "Corolla");
car.start(); // logs "The vehicle is starting"
car.drive(); // logs "The car is driving"

const truck = new Truck("Ford", "F-150");
truck.start(); // logs "The vehicle is starting"
truck.haul(); // logs "The truck is hauling"

const plane = new Plane("Boeing", "747");
plane.start(); // logs "The vehicle is starting"
plane.fly(); // logs "The plane is flying"
```
</details>


6. Add a `color` property to the `Vehicle` constructor, and modify each subclass to accept a `color` parameter in the constructor.

<details>
  <summary>Answer</summary>

```javascript
function Vehicle(make, model, color) {
  this.make = make;
  this.model = model;
  this.color = color;
}

Vehicle.prototype.start = function() {
  console.log("The vehicle is starting");
};

function Car(make, model, color) {
  Vehicle.call(this, make, model, color);
  this.numWheels = 4;
}

Car.prototype = Object.create(Vehicle.prototype);
Car.prototype.constructor = Car;

Car.prototype.drive = function() {
  console.log("The car is driving");
};

function Truck(make, model, color) {
  Vehicle.call(this, make, model, color);
  this.numWheels = 6;
}

Truck.prototype = Object.create(Vehicle.prototype);
Truck.prototype.constructor = Truck;

Truck.prototype.haul = function() {
  console.log("The truck is hauling");
};

function Plane(make, model, color) {
  Vehicle.call(this, make, model, color);
  this.numWings = 2;
}

Plane.prototype = Object.create(Vehicle.prototype);
Plane.prototype.constructor = Plane;

Plane.prototype.fly = function() {
  console.log("The plane is flying");
};
```
</details>
