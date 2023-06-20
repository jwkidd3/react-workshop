# Session 6 - Part 2: useEffect Hook in React

The `useEffect` hook is a built-in hook in React that allows you to perform side effects in your functional components. Side effects are anything that affects something outside of the component, such as fetching data from an API, updating the document title, or adding event listeners.

## Why Use useEffect?

In React, when a component's state or props change, the component is re-rendered. This means that the component's render function is called again, and the component's DOM is updated to reflect the new state or props.

However, sometimes you want to perform some actions only when the component mounts, and not every time it re-renders. For example, you may want to fetch some data from an API when the component mounts, but not every time the component re-renders.

If you don't use `useEffect`, you may end up with unwanted side effects that happen every time the component re-renders. This can lead to performance issues and unexpected behavior.

## Using useEffect to Solve the Problem

`useEffect` allows you to perform side effects only when certain dependencies have changed. For example, you can use `useEffect` to fetch data from an API only when the component mounts, by passing an empty dependency array as the second argument:

```jsx
import { useState, useEffect } from 'react';

function MyComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    async function fetchData() {
      const response = await fetch('https://myapi.com/data');
      const json = await response.json();
      setData(json);
    }

    fetchData();
  }, []);

  return (
    <div>
      {data ? (
        <ul>
          {data.map(item => (
            <li key={item.id}>{item.name}</li>
          ))}
        </ul>
      ) : (
        <p>Loading...</p>
      )}
    </div>
  );
}
```

In this example, we're using `useEffect` to fetch data from an API when the component mounts, by passing an empty array as the second argument. This means that the effect will only run once, when the component mounts.

If we didn't use `useEffect`, the `fetchData` function would be called every time the component re-renders, which could lead to performance issues and unnecessary API requests.

`useEffect` also allows you to clean up after an effect, by returning a cleanup function:

```jsx
import { useState, useEffect } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;

    return () => {
      document.title = 'My App';
    };
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

In this example, we're using `useEffect` to update the document title when the count changes, and returning a cleanup function that resets the title when the component unmounts.

Using `useEffect` allows us to perform side effects in a controlled and predictable way, which can improve the performance and stability of our React applications.

## Some simple use cases

Here are some more common use cases of `useEffect`:

### Setting up Event Listeners

You can use `useEffect` to set up event listeners in your component. Here's an example:

```jsx
import { useState, useEffect } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    function handleClick() {
      setCount(count + 1);
    }

    window.addEventListener('click', handleClick);

    return () => {
      window.removeEventListener('click', handleClick);
    };
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
    </div>
  );
}
```

In this example, we're using `useEffect` to set up a click event listener on the window object. We're incrementing the count state every time the window is clicked, and removing the event listener when the component unmounts.

### Initializing Third-Party Libraries

You can use `useEffect` to initialize third-party libraries in your component. Here's an example:

```jsx
import { useState, useEffect } from 'react';
import ThirdPartyLib from 'third-party-lib';

function MyComponent() {
  const [thirdPartyInstance, setThirdPartyInstance] = useState(null);

  useEffect(() => {
    const instance = new ThirdPartyLib();

    setThirdPartyInstance(instance);

    return () => {
      instance.destroy();
    };
  }, []);

  return (
    <div>
      <p>Third-party library initialized: {thirdPartyInstance !== null ? 'yes' : 'no'}</p>
    </div>
  );
}
```

In this example, we're using `useEffect` to initialize a third-party library when the component mounts. We're using `useState` to manage the state of the third-party instance, and updating the state with the initialized instance in the effect.

We're passing an empty array as the second argument to `useEffect`, which means that the effect will only run once, when the component mounts. We're also returning a cleanup function from the effect that calls the `destroy` method on the third-party instance to clean up after the effect.

Using `useEffect` to initialize third-party libraries is a common use case of the hook, and can help you manage side effects in your React components.

## Exercises

### Exercise 1

#### Goal

In this exercise, we will fetch data from an external API and display it on the screen using `useEffect`.

#### Instructions

1.  Create a new React component called `DataFetching`.
2.  Inside the component, create a state variable called `data` with an empty object as its initial value.
3.  Use the `useEffect` hook to fetch data from the following API endpoint: `https://jsonplaceholder.typicode.com/todos/1`
4.  When the data is fetched, update the `data` state variable with the fetched data.
5.  Display the data on the screen.

#### Starter Code

```jsx
import {
	useEffect,
	useState
} from 'react';

function DataFetching() { 
  // TODO: create state variable for data   
	useEffect(() => { 
    // TODO: fetch data and update state variable
	}, []);
	return (
     // TODO: display data on the screen
	);
}
```

* * *

### Exercise 2

#### Goal

In this exercise, we will change the title of the webpage using `useEffect`.

#### Instructions

1.  Create a new React component called `PageTitle`.
2.  Inside the component, create a state variable called `count` with a value of `0`.
3.  Use the `useEffect` hook to update the title of the webpage with the current value of `count`.
4.  Create a button that increments the `count` state variable when clicked.
5.  Display the `count` state variable on the screen.

#### Starter Code

```jsx
import {
	useEffect,
	useState
} from 'react';

function PageTitle() {
	// TODO: create state variable for count
	useEffect(() => { 
    // TODO: update title of webpage with current value of count
	}, [count]);

	return ( < div >
			// TODO: create button that increments count when clicked
      // TODO: display count on the screen
			</div>   );
}
```

* * *

### Exercise 3

#### Goal

In this exercise, we will log a message to the console using `useEffect`.

#### Instructions

1.  Create a new React component called `ConsoleLogger`.
2.  Use the `useEffect` hook to log the message "Component mounted" to the console when the component is mounted.
3.  Use the `useEffect` hook to log the message "Component updated" to the console when the component is updated.

#### Starter Code

```jsx
import {
	useEffect
} from 'react';

function ConsoleLogger() {
	useEffect(() => {
		console.log('Component mounted');
	}, []);
	useEffect(() => {
		console.log('Component updated');
	});
	return null;
}
```