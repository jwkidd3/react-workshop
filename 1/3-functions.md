# Session 1 - Part 3: Functions


In JavaScript, a function is a block of code that can be executed when called. Functions allow you to encapsulate a piece of logic and reuse it throughout your code. Functions can accept inputs (arguments) and return an output (return value).

Functions can be declared in several ways in JavaScript:

*   Function declaration:

```js
function greet(name) {
	console.log(`Hello, ${name}!`);
}
greet('John'); // Output: Hello, John!
```

*   Function expression:

```js
const greet = function(name) {
	console.log(`Hello, ${name}!`);
};
greet('John'); // Output: Hello, John!
```

*   Arrow function:

```js
const greet = (name) => {
	console.log(`Hello, ${name}!`);
};
greet('John'); // Output: Hello, John!
```

In this example, the `greet` function accepts a single argument `name` and logs a greeting message to the console. The function can be called by invoking the function name followed by parentheses and passing in the required arguments.

Functions can also return a value using the `return` statement:

```js
const add = (a, b) => {
	return a + b;
};
console.log(add(1, 2)); // Output: 3
```

In this example, the `add` function accepts two arguments `a` and `b` and returns their sum. The function can be called by invoking the function name followed by parentheses and passing in the required arguments. The return value can be stored in a variable or used directly in an expression.

Functions are a fundamental building block of JavaScript and are used extensively in building applications. In the next part, we'll look at some examples of using functions in JavaScript.

## Exercises

1.  Create a function that takes two numbers as arguments and returns the sum of those numbers.
    
2.  Create a function that takes an array of numbers as an argument and returns the average of those numbers.
    
3.  Create a function that takes a string as an argument and returns the number of vowels in that string.
    
4.  Create a function that takes two strings as arguments and returns `true` if the first string ends with the second string, and `false` otherwise.
    
5.  Create a function that takes an array of strings as an argument and returns a new array with only the strings that are longer than 5 characters.
    
6.  Create a function that takes an object as an argument and returns a new object with only the properties that have values of type `string`.
    
7.  Create a function that takes two objects as arguments and returns a new object that combines the properties of both objects. If a property exists in both objects, the value from the second object should overwrite the value from the first object.
    

These exercises are designed to help you practice using functions in JavaScript. The goal is to gain a deeper understanding of how functions work and how they can be used to solve problems.