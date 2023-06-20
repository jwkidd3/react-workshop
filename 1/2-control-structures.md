# Session 1 - Part 2: Control Structures

## If Statements

In JavaScript, we use `if` statements to execute code if a condition is true. Here's an example:

```javascript
var x = 10;

if (x > 5) {
  console.log("x is greater than 5");
}
```

In this example, we've created a variable `x` with the value of 10. We then use an `if` statement to check if `x` is greater than 5. If it is, we print the message "x is greater than 5" to the console.

## Else Statements

We can also use `else` statements with `if` statements to execute code if the condition is false. Here's an example:

```javascript
var x = 2;

if (x > 5) {
  console.log("x is greater than 5");
} else {
  console.log("x is less than or equal to 5");
}
```

In this example, we've created a variable `x` with the value of 2. We use an `if` statement to check if `x` is greater than 5. If it is not, we execute the code in the `else` block and print the message "x is less than or equal to 5" to the console.

## Else-If Statements

We can also use `else-if` statements with `if` statements to check additional conditions. Here's an example:

```javascript
var x = 0;

if (x > 0) {
  console.log("x is positive");
} else if (x < 0) {
  console.log("x is negative");
} else {
  console.log("x is zero");
}
```

In this example, we've created a variable `x` with the value of 0. We use an `if` statement to check if `x` is greater than 0. If it is not, we check if it is less than 0 using the `else-if` statement. If it is neither greater than nor less than 0, we execute the code in the `else` block and print the message "x is zero" to the console.

## Switch Statements

We can use `switch` statements to perform different actions based on different conditions. Here's an example:

```javascript
var color = "red";

switch (color) {
  case "red":
    console.log("Color is red");
    break;
  case "blue":
    console.log("Color is blue");
    break;
  default:
    console.log("Color is not red or blue");
}
```

In this example, we've created a variable `color` with the value of "red". We use a `switch` statement to check the value of `color`. If it is "red", we print the message "Color is red" to the console. If it is "blue", we print the message "Color is blue" to the console. If it is neither "red" nor "blue", we execute the code in the `default` block and print the message "Color is not red or blue" to the console.

## For Loops

We use `for` loops to execute code multiple times. Here's an example:

```javascript
for (var i = 0; i < 5; i++) {
  console.log("The value of i is " + i);
}
```

In this example, we use a `for` loop to execute the code inside the curly braces 5 times. We start with the value of `i` set to 0. We then check if `i` is less than 5. If it is, we execute the code inside the curly braces, which prints the message "The value of i is " followed by the value of `i`, to the console. We then increment the value of `i` by 1, and the loop starts again until `i` is no longer less than 5.

We can also use `for` loops to iterate over arrays. Here's an example:

```javascript
var colors = ["red", "blue", "green"];

for (var i = 0; i < colors.length; i++) {
  console.log("The color at index " + i + " is " + colors[i]);
}
```

In this example, we've created an array called `colors` with three elements. We use a `for` loop to iterate over each element of the array. We start with the value of `i` set to 0. We then check if `i` is less than the length of the `colors` array. If it is, we execute the code inside the curly braces,
