# Session 1 - Part 1: Variables and Data Types

## Variables

In JavaScript, variables are used to store data values. To create a variable, we use the `var`, `let`, or `const` keyword followed by the name of the variable. Here's an example:

```javascript
var myVariable = "Hello, world!";
```

In this example, we've created a variable called `myVariable` and assigned it the value of the string "Hello, world!".

## Data Types

JavaScript has several built-in data types:

- Strings: A sequence of characters enclosed in quotes, either single or double.
- Numbers: Integers or floating-point numbers.
- Booleans: A true/false value.
- Null: A special value indicating the absence of any object value.
- Undefined: A special value indicating the absence of any value.
- Objects: A collection of related data.
- Arrays: A collection of related data stored in a list.

Here are some examples of how to create and use different data types in JavaScript:

```javascript
// Strings
var greeting = "Hello, world!";

// Numbers
var age = 30;
var price = 9.99;

// Booleans
var isComplete = true;

// Null and Undefined
var x = null;
var y;

// Objects
var person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  isMarried: false
};

// Arrays
var fruits = ["apple", "banana", "orange"];
```

## Numbers

In JavaScript, there is only one type of number, which can be either an integer or a floating-point number. Here are some examples:

```javascript
var myInteger = 42;
var myFloat = 3.14;
```

You can perform arithmetic operations on numbers using the standard operators: `+` for addition, `-` for subtraction, `*` for multiplication, and `/` for division. Here are some examples:

```javascript
var sum = 2 + 2; // 4
var difference = 10 - 5; // 5
var product = 3 * 4; // 12
var quotient = 10 / 2; // 5
```

You can also use the `%` operator to get the remainder of a division operation:

```javascript
var remainder = 10 % 3; // 1
```

## Exercises

Create a JavaScript file and declare a variable using the `let` keyword. Assign it a numeric value of your choice, and then use the `console.log()` method to print the value of the variable to the console. 

Next, create two more numeric variables and perform an arithmetic operation of your choice using the operators `+`, `-`, `*`, or `/`. Then, use the `console.log()` method to print the result of the operation to the console.

Finally, create an array of numbers and use the `map()` method to multiply each element by a number of your choice. Then, use the `console.log()` method to print the resulting array to the console.

Congratulations, you've completed the first part of Session 1: Introduction to JavaScript and ES6! In the next part, we'll cover control structures.
