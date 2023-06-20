# Session 2 - Part 1: Scope and Closures

In JavaScript, scope determines the accessibility of variables and functions in different parts of your code. Understanding scope is important for writing clean, efficient, and bug-free code.

## Block Scope

Block scope refers to the idea that variables declared inside a block (i.e. inside curly braces) are only accessible within that block.

Here's an example using `let` and `const`:

```javascript
function myFunction() {
  if (true) {
    let myVar = "Hello";
    const myConst = "World";
    console.log(myVar); // logs "Hello"
    console.log(myConst); // logs "World"
  }
  console.log(myVar); // throws an error because myVar is not defined
  console.log(myConst); // throws an error because myConst is not defined
}

myFunction();
```

In this example, we declare a variable `myVar` using `let` and a constant `myConst` using `const` inside the block created by the `if` statement. Since we used `let` and `const`, `myVar` and `myConst` are only accessible within the block. If we try to access them outside the block, we'll get an error because they're not defined. This is an example of **block scope**.

## Function Scope

Function scope refers to the idea that variables declared inside a function are only accessible within that function.

Here's an example using `let`:

```javascript
function myFunction() {
  let myVar = "Hello";
  console.log(myVar); // logs "Hello"
}

myFunction();
console.log(myVar); // throws an error because myVar is not defined
```

In this example, we declare a variable `myVar` using `let` inside the function `myFunction`. We can access `myVar` inside the function, but if we try to access it outside the function, we'll get an error because it's not defined. This is an example of **function scope**.

## Closures

A closure is a function that has access to variables in its outer (enclosing) function scope, even after the outer function has returned. 

Here's an example using `const`:

```javascript
function outerFunction() {
  const outerVar = "Hello";

  function innerFunction() {
    console.log(outerVar);
  }

  return innerFunction;
}

const myFunction = outerFunction();
myFunction(); // logs "Hello"
```

In this example, `outerFunction` returns `innerFunction`, which is then assigned to `myFunction`. Even though `outerFunction` has returned and is no longer running, `myFunction` still has access to the `outerVar` variable, which logs "Hello" to the console. This is an example of a **closure**.

Here's another example using a closure:

```javascript
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

const add5 = makeAdder(5);
const add10 = makeAdder(10);

console.log(add5(2)); // logs 7
console.log(add10(2)); // logs 12
```

In this example, we create a function `makeAdder` that returns another function. The returned function has access to the `x` parameter from the outer function's scope, even after `makeAdder` has returned. We then create two functions (`add5` and `add10`) using `makeAdder` and call them with the argument `2`. The first call (`add5(2)`) returns `7` and the second call (`add10(2)`) returns `12`. This is another example of a **closure**.

## Exercises

1. Write a function that takes a number as input and returns a function that, when called, adds the input number to the number passed to it as an argument. Use a closure to achieve this.

<details>
<summary>Answer</summary>

:white_check_mark: Answer is **4**
```javascript
function addNumber(x) {
  return function(y) {
    return x + y;
  };
}
const add5 = addNumber(5);
console.log(add5(2)); // logs 7
```
</details>



2. Write a function that takes an array of numbers as input and returns a function that, when called, returns the sum of all the numbers in the array. Use a closure to achieve this.

<details>
  <summary>Answer</summary>

  ```javascript
  function sumArray(numbers) {
    return function() {
      let sum = 0;
      for (let i = 0; i < numbers.length; i++) {
        sum += numbers[i];
      }
      return sum;
    };
  }

  const addNumbers = sumArray([1, 2, 3]);
  console.log(addNumbers()); // logs 6
  ```
</details>


3. Write a function that takes a string as input and returns a function that, when called, returns a new string that is the original string repeated n times, where n is an argument passed to the returned function. Use a closure to achieve this.

<details>
  <summary>Answer</summary>

  ```javascript
    function repeatString(str) {
      return function(n) {
        let result = "";
        for (let i = 0; i < n; i++) {
          result += str;
        }
        return result;
      };
    }

    const repeatHello = repeatString("Hello");
    console.log(repeatHello(3)); // logs "HelloHelloHello"
  ```
</details>

