# Session 6 - Part 4: React Component Life cycles with `useEffect` Hook

In React, components go through various lifecycle phases, such as initialization, rendering, updating, and unmounting. These lifecycle phases correspond to specific methods that can be used to perform various tasks, such as setting up state, fetching data, or interacting with external APIs. With the `useEffect` hook, we can simulate some of these lifecycle methods in functional components.

## ComponentDidMount with useEffect Hook

In React, `componentDidMount` is a lifecycle method that is called when a component is first mounted to the DOM. We can simulate this behavior in functional components using the `useEffect` hook.

## Simulating `componentDidMount` with `useEffect`

To simulate `componentDidMount` using `useEffect`, we can pass an empty array `[]` as the second argument to the `useEffect` hook. This ensures that the effect function will only run once, when the component is first mounted. Here's an example:

```jsx
import {
	useEffect
} from 'react';

function ComponentDidMount() {
	useEffect(() => {
		console.log('Component mounted');
	}, []);

	return <div>
    Component has mounted 
  </div>; 
}
```

In this example, the `useEffect` hook is used to log a message to the console when the component is first mounted. The empty array `[]` passed as the second argument to `useEffect` ensures that the effect function only runs once, when the component is first mounted.

### Real-World Examples

Here are some real-world examples of using the `useEffect` hook to simulate `componentDidMount` in functional components:

#### Fetching Data from an API

```jsx
import { useState, useEffect } from "react";
function DataFetcher() {
  const [data, setData] = useState(null);
  useEffect(() => {
    async function fetchData() {
      const response = await fetch("https://api.example.com/data");
      const data = await response.json();
      setData(data);
    }
    fetchData();
  }, []);
  if (!data) {
    return;
    <div> Loading... </div>;
  }
  return (
    <div>
      {" "}
      <h1>{data.title}</h1> <p> {data.description} </p>{" "}
    </div>
  );
}

```

In this example, the `useEffect` hook is used to fetch data from an external API when the component is first mounted. The `setData` function is used to update the component's state with the fetched data. The conditional rendering ensures that a "Loading..." message is displayed while the data is being fetched.

#### Initializing a Third-Party Library

```jsx
import { useState, useEffect } from "react";
import ThirdPartyLibrary from "third-party-library";
function ThirdPartyComponent() {
  const [libraryInstance, setLibraryInstance] = useState(null);
  useEffect(() => {
    const newLibraryInstance = new ThirdPartyLibrary();
    setLibraryInstance(newLibraryInstance);
  }, []);
  if (!libraryInstance) {
    return <div>Loading...</div>;
  }
  return (
    <div>
      {" "}
      <h1>{libraryInstance.getTitle()}</h1>{" "}
      <p>{libraryInstance.getDescription()}</p>{" "}
    </div>
  );
}

```

In this example, the `useEffect` hook is used to initialize a third-party library when the component is first mounted. The `setLibraryInstance` function is used to update the component's state with the library instance. The conditional rendering ensures that a "Loading..." message is displayed while the library is being initialized.


ComponentDidUpdate with useEffect Hook

In React, `componentDidUpdate` is a lifecycle method that is called whenever a component is updated, after the render method is called. We can simulate this behavior in functional components using the `useEffect` hook.

## Simulating `componentDidUpdate` with `useEffect`

To simulate `componentDidUpdate` using `useEffect`, we can pass an array of dependencies as the second argument to the `useEffect` hook. The effect function will be re-executed whenever any of the dependencies change. Here's an example:

```jsx
import { useState, useEffect } from "react";
function ComponentDidUpdate() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    console.log(`Count is now ${count}`);
  }, [count]);
  const handleIncrement = () => {
    setCount(count + 1);
  };
  return (
    <div>
      {" "}
      <h1>{count}</h1> <button onClick={handleIncrement}>Increment</button>{" "}
    </div>
  );
}
```

In this example, the `useEffect` hook is used to log a message to the console whenever the `count` state variable changes. The `[count]` dependency array passed as the second argument to `useEffect` ensures that the effect function is re-executed whenever the `count` variable changes.

### Real-World Examples

Here are some real-world examples of using the `useEffect` hook to simulate `componentDidUpdate` in functional components:

#### Updating the Document Title

```jsx
import { useState, useEffect } from "react";
function DocumentTitleUpdater() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);
  const handleIncrement = () => {
    setCount(count + 1);
  };
  return (
    <div>
      {" "}
      <h1>{count}</h1> <button onClick={handleIncrement}>Increment</button>{" "}
    </div>
  );
}
```

In this example, the `useEffect` hook is used to update the document title whenever the `count` state variable changes. The `[count]` dependency array passed as the second argument to `useEffect` ensures that the effect function is re-executed whenever the `count` variable changes.

#### Animating Elements

```jsx
import { useState, useEffect } from "react";
function ElementAnimator() {
  const [isVisible, setIsVisible] = useState(false);
  useEffect(() => {
    const timer = setTimeout(() => {
      setIsVisible(true);
    }, 1000);
    return () => {
      clearTimeout(timer);
    };
  }, []);
  useEffect(() => {
    const element = document.getElementById("animated-element");
    if (isVisible) {
      element.style.opacity = 1;
      element.style.transform = "translateY(0)";
    } else {
      element.style.opacity = 0;
      element.style.transform = "translateY(50px)";
    }
  }, [isVisible]);
  return (
    <div>
      {" "}
      <div
        id="animated-element"
        style={{
          opacity: 0,
          transform: "translateY(50px)",
          transition: "all 1s ease",
        }}
      >
        {" "}
        Animated Element{" "}
      </div>{" "}
    </div>
  );
}
```

ComponentWillUnmount with useEffect Hook

In React, `componentWillUnmount` is a lifecycle method that is called just before a component is unmounted from the DOM. We can simulate this behavior in functional components using the `useEffect` hook.

## Simulating `componentWillUnmount` with `useEffect`

To simulate `componentWillUnmount` using `useEffect`, we can return a cleanup function from the effect. The cleanup function will be called just before the effect is re-executed or when the component is unmounted. Here's an example:

```jsx
import { useState, useEffect } from "react";
function ComponentWillUnmount() {
  const [visible, setVisible] = useState(true);
  useEffect(() => {
    return () => {
      console.log("Component unmounted");
    };
  }, []);
  const handleClick = () => {
    setVisible(false);
  };
  return (
    <div>
      {" "}
      {visible && <button onClick={handleClick}>Hide</button>}{" "}
      <div>Component is {visible ? "visible" : "hidden"}</div>{" "}
    </div>
  );
}
```

In this example, the `useEffect` hook is used to log a message to the console when the component is unmounted. The cleanup function is returned from the effect by omitting the dependencies array (`[]`) as the second argument to `useEffect`.

### Real-World Examples

Here are some real-world examples of using the `useEffect` hook to simulate `componentWillUnmount` in functional components:

#### Unsubscribing from an Event Listener

```jsx
import { useEffect } from "react";
function EventListenerComponent() {
  useEffect(() => {
    const handleClick = () => {
      console.log("Button clicked");
    };
    document.addEventListener("click", handleClick);
    return () => {
      document.removeEventListener("click", handleClick);
    };
  }, []);
  return <button>Click me</button>;
}
```

In this example, the `useEffect` hook is used to add an event listener to the document when the component is first mounted, and remove the event listener when the component is unmounted. The cleanup function is returned from the effect by removing the event listener using `removeEventListener`.

#### Cleaning Up a Timer

```jsx
import { useState, useEffect } from "react";
function TimerComponent() {
  const [time, setTime] = useState(0);
  useEffect(() => {
    const timer = setInterval(() => {
      setTime(time + 1);
    }, 1000);
    return () => {
      clearInterval(timer);
    };
  }, [time]);
  return <div>Time elapsed: {time} seconds</div>;
}
```

In this example, the `useEffect` hook is used to create a timer that increments the `time` state variable every second. The cleanup function is returned from the effect by clearing the interval using `clearInterval`. This ensures that the timer is cleaned up when the component is unmounted.