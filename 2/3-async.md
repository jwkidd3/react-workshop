# Session 2 - Part 3: Async Programming with Promises and Async/Await

## 1. Callbacks

Callbacks are functions that are passed as arguments to other functions, which are then invoked at some point during the execution of the function that accepts them.

Callbacks are often used in asynchronous programming, where a function needs to perform an operation that may take some time to complete, such as making a network request or reading a file from disk. Rather than blocking the execution of the program while waiting for the operation to complete, the function can accept a callback that will be called once the operation has finished.

Here's an example of a callback function:

```javascript
function sayHello(name, callback) {
  const message = `Hello, ${name}!`;
  callback(message);
}

function logMessage(message) {
  console.log(message);
}

sayHello("John", logMessage); // logs "Hello, John!"
```

In the above example, we define a function `sayHello` that takes two arguments: a `name` and a `callback` function. The `sayHello` function creates a `message` string by concatenating the `name` with the string "Hello, ", and then passes this `message` to the `callback` function. Finally, we call the `sayHello` function, passing in the name "John" and the `logMessage` function as the callback. This results in the message "Hello, John!" being logged to the console.

Here's another example that shows how callbacks can be used to perform an asynchronous operation:

```javascript
function fetchUser(username, callback) {
  const url = `https://api.github.com/users/${username}`;
  fetch(url)
    .then(response => response.json())
    .then(user => callback(user))
    .catch(error => console.error(error));
}

fetchUser("octocat", user => console.log(user)); // logs the octocat user object
```

In this example, we define a function `fetchUser` that takes a `username` and a `callback` function as arguments. The `fetchUser` function creates a URL for the GitHub API, makes a `fetch` request to that URL, and then calls the `callback` function with the user object that is returned from the API.

We then call the `fetchUser` function, passing in the username "octocat" and a callback that logs the user object to the console.

Note that the `fetch` method returns a Promise, so we use the `then` method to handle the response from the API and call the `callback` function with the user object. If there is an error, we log it to the console using the `catch` method.

Callbacks are a fundamental concept in asynchronous programming, and are used extensively in JavaScript and many other programming languages.

## 2. Promises

Promises are a more recent addition to JavaScript, and provide a cleaner and more flexible way to work with asynchronous code. A Promise represents a value that may not be available yet, but will be resolved at some point in the future.

Here's an example of a Promise:

```javascript
const promise = new Promise((resolve, reject) => {
  const result = Math.random();
  if (result < 0.5) {
    resolve(result);
  } else {
    reject(new Error("Result is too high!"));
  }
});

promise
  .then(result => console.log(`Result: ${result}`))
  .catch(error => console.error(error));
```

In this example, we create a new Promise that generates a random number between 0 and 1, and then resolves the Promise with that number if it is less than 0.5, or rejects the Promise with an error if it is greater than or equal to 0.5.

We then attach two handlers to the Promise using the `then` and `catch` methods. The `then` method is called with the resolved value of the Promise, and the `catch` method is called with any error that occurs.

Promises are a powerful tool for working with asynchronous code, and provide a number of features that make it easier to manage complex operations. For example, Promises can be chained together using the `then` method, allowing multiple asynchronous operations to be performed in sequence. Promises also support error handling using the `catch` method, which can be used to gracefully handle any errors that occur during the execution of the Promise.

## 3. Async/Await

Async/Await is a more recent addition to JavaScript, and provides a way to write asynchronous code that looks and behaves like synchronous code. Async/Await is built on top of Promises, and provides a cleaner and more readable syntax for working with them.

Here's an example of using Async/Await to perform an asynchronous operation:

```javascript
async function fetchUser(username) {
  const url = `https://api.github.com/users/${username}`;
  const response = await fetch(url);
  const user = await response.json();
  return user;
}

fetchUser("octocat")
  .then(user => console.log(user))
  .catch(error => console.error(error));
```

In this example, we define an asynchronous function `fetchUser` that takes a `username` as its argument. The `fetchUser` function creates a URL for the GitHub API, uses the `await` keyword to make a `fetch` request to that URL, and then uses `await` again to parse the response as JSON.

Finally, the `fetchUser` function returns the user object, which is then logged to the console using the `then` method. If there is an error, it is logged to the console using the `catch` method.

Async/Await provides a cleaner and more intuitive way to work with asynchronous code, and is becoming increasingly popular in modern JavaScript development. However, it's important to remember that Async/Await is built on top of Promises, and that Promises are still a fundamental part of asynchronous programming in JavaScript.

## Exercises

1. Write a function called `fetchJson` that takes a URL as its argument and returns a Promise that resolves with the JSON data from the URL. For example, `fetchJson("https://jsonplaceholder.typicode.com/todos/1")` should return a Promise that resolves with the todo item with ID 1.


<details>
  <summary>Answer</summary>

```js
function fetchJson(url) {
  return fetch(url).then(response => response.json());
}
```
</details>

2. Write a function called `fetchJsonRetry` that takes a URL as its argument and returns a Promise that resolves with the JSON data from the URL. If the fetch fails, the function should retry the fetch up to three times, with a delay of one second between each retry. For example, `fetchJsonRetry("https://jsonplaceholder.typicode.com/todos/1")` should return a Promise that resolves with the todo item with ID 1.


<details>
  <summary>Answer</summary>

```js
  function fetchJsonRetry(url) {
    return new Promise((resolve, reject) => {
      let retries = 0;
      const doFetch = () => {
        fetch(url)
          .then(response => response.json())
          .then(resolve)
          .catch(error => {
            retries++;
            if (retries < 3) {
              setTimeout(doFetch, 1000);
            } else {
              reject(error);
            }
          });
      };
      doFetch();
    });
  }
```
</details>

3. Write a function called `fetchJsonParallel` that takes an array of URLs as its argument and returns a Promise that resolves with an array of the JSON data from each URL. The fetches should be done in parallel, using Promise.all. For example, `fetchJsonParallel(["https://jsonplaceholder.typicode.com/todos/1", "https://jsonplaceholder.typicode.com/todos/2"])` should return a Promise that resolves with an array containing the todo items with IDs 1 and 2.

<details>
  <summary>Answer</summary>

```js
function fetchJsonParallel(urls) {
  const promises = urls.map(url => fetch(url).then(response => response.json()));
  return Promise.all(promises);
}
```
</details>

4. Write a function called `fetchJsonSequence` that takes an array of URLs as its argument and returns a Promise that resolves with an array of the JSON data from each URL. The fetches should be done in sequence, using async/await. For example, `fetchJsonSequence(["https://jsonplaceholder.typicode.com/todos/1", "https://jsonplaceholder.typicode.com/todos/2"])` should return a Promise that resolves with an array containing the todo items with IDs 1 and 2.


<details>
  <summary>Answer</summary>

```js
async function fetchJsonSequence(urls) {
  const results = [];
  for (const url of urls) {
    const response = await fetch(url);
    const data = await response.json();
    results.push(data);
  }
  return results;
}
```
</details>

5. Write a function called `createRace` that takes an array of Promises as its argument and returns a Promise that resolves with the result of the first Promise that resolves. For example, `createRace([fetchJson("https://jsonplaceholder.typicode.com/todos/1"), new Promise(resolve => setTimeout(() => resolve("Hello, world!"), 500))])` should return a Promise that resolves with the todo item with ID 1, because that fetch will resolve first.


<details>
  <summary>Answer</summary>

```js
function createRace(promises) {
  return Promise.race(promises);
}
```
</details>

6. Write a function called `createTimeout` that takes a Promise and a time limit (in milliseconds) as its arguments and returns a new Promise that resolves with the same result as the input Promise, if the input Promise resolves within the time limit. If the input Promise does not resolve within the time limit, the new Promise should reject with an error message. For example, `createTimeout(fetchJson("https://jsonplaceholder.typicode.com/todos/1"), 500)` should return a Promise that rejects with an error message after 500 milliseconds if the fetch has not completed by then.

<details>
  <summary>Answer</summary>

```js
function createTimeout(promise, timeLimit) {
  let timeout;
  const timeoutPromise = new Promise((resolve, reject) => {
    timeout = setTimeout(() => {
      reject(`Timed out after ${timeLimit} milliseconds`);
    }, timeLimit);
  });
  return Promise.race([promise, timeoutPromise]).finally(() => clearTimeout(timeout));
}
```
</details>

