# Session 3 - Part 3: Export/Require in NodeJS

In NodeJS, the `require` function and the `module.exports` object provide a way to include code from one module into another module. This allows you to break up your code into smaller, more manageable pieces, and to reuse code across multiple modules.

The `module.exports` object is used to export values or functions from a module, making them available for other modules to require. For example, the following code exports a function named `add` from a module:

```js
// math.js 
function add(a, b) {
	return a + b;
}
module.exports = add;
```

The `require` function is used to import values or functions from another module into the current module. For example, the following code requires the `add` function from the `math` module:

```js
// index.js
const add = require('./math');
console.log(add(1, 2));
```

When the `index.js` file is executed, it will require the `add` function from the `math` module and use it to log the result of `1 + 2` to the console.

In addition to exporting and requiring individual values or functions, you can also use `exports.sth` to export values. For example, the following code exports multiple functions using `exports.sth`:

```js
// math.js  
function add(a, b) {
	return a + b;
}

function subtract(a, b) {
	return a - b;
}
exports.add = add;
exports.subtract = subtract;
```

And the following code requires the multiple functions from the `math` module:

```js
// index.js
const math = require('./math');
console.log(math.add(1, 2));
console.log(math.subtract(1, 2));
```

These examples demonstrate the basic usage of `require` and `module.exports` in NodeJS for including code from one module into another. By breaking up your code into smaller, more manageable pieces and reusing code across multiple modules, you can write cleaner, more maintainable code.


## Examples

Here are some examples to help you understand the usage of `require` and `module.exports` in NodeJS.

### Example 1: Exporting and requiring multiple functions using `module.exports`

In this example, we will export multiple functions `add` and `multiply` from the `math.js` module using `module.exports` and require them in the `index.js` module.

```js
// math.js 
function add(a, b) {
	return a + b;
}

function multiply(a, b) {
	return a * b;
}
module.exports = {
	add,
	multiply
};
```

```js
// index.js

const {
	add,
	multiply
} = require('./math');
console.log(add(1, 2));
console.log(multiply(3, 4));
```

When we run the `index.js` file, it will require the `add` and `multiply` functions from the `math.js` module and log the results of `1 + 2` and `3 * 4` to the console, which are `3` and `12`, respectively.

### Example 2: Exporting and requiring multiple functions using `exports.sth`

In this example, we will export multiple functions `divide` and `square` from the `math.js` module using `exports.sth` and require them in the `index.js` module.

```js
// math.js  
function divide(a, b) {
	return a / b;
}

function square(a) {
	return a * a;
}
exports.divide = divide;
exports.square = square;
```

```js
// index.js 
const {
	divide,
	square
} = require('./math');
console.log(divide(6, 2));
console.log(square(5));
```

When we run the `index.js` file, it will require the `divide` and `square` functions from the `math.js` module and log the results of `6 / 2` and `5 * 5` to the console, which are `3` and `25`, respectively.

## Exercises

Here are some exercises to help you practice using `require` and `module.exports` in NodeJS:

1.  Create two modules: `greet.js` and `index.js`. In the `greet.js` module, export a function named `greet` that takes a name as an argument and returns a greeting message with the name. In the `index.js` module, require the `greet` function from the `greet.js` module and use it to log a greeting message for your name to the console.
    
2.  Create two modules: `math.js` and `index.js`. In the `math.js` module, export two functions named `add` and `subtract` that take two numbers as arguments and return their sum and difference, respectively. In the `index.js` module, require the `add` and `subtract` functions from the `math.js` module and use them to log the results of a few mathematical operations to the console.
    
3.  Create two modules: `person.js` and `index.js`. In the `person.js` module, export an object literal named `person` with properties for a person's name, age, and address. In the `index.js` module, require the `person` object from the `person.js` module and use it to log the person's information to the console.
    

These exercises will help you get more practice using `require` and `module.exports` in NodeJS, and give you a deeper understanding of how to include code from one module into another in NodeJS.