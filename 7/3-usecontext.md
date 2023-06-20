# Session 7 - Part 3: useContext Hook

In React, passing data from a parent component to its child components through props is a common practice. However, this can become a problem when data needs to be passed down through multiple levels of components, resulting in what is known as prop drilling. While prop drilling is a major issue, it is not the only problem that can arise from passing data through props. Other problems include naming conflicts, complexity, and performance issues.

To solve these problems, React introduced the `useContext` hook, which provides a way to share data across the component tree without the need for intermediate components to pass the data down through props. This allows for a cleaner and more maintainable codebase, and can help to avoid issues such as naming conflicts, complexity, and performance problems.

## Creating a Context

A context is created using the `createContext()` method, which returns a context object. This context object can be used to provide a value to child components, and can also be used by child components to access that value. Here's an example:

```jsx
import { createContext } from "react";
const MyContext = createContext();
```

In this example, we create a context object called `MyContext` using `createContext()`.

## Providing a Value with a Provider

To provide a value to child components, we use the `Provider` component that comes with the context object. Here's an example:

```jsx
<MyContext.Provider value={myValue}>
  {" "}
  <ChildComponent />{" "}
</MyContext.Provider>;
```

In this example, we provide a value to the `ChildComponent` component by wrapping it in the `Provider` component and passing the value as a prop.

## Accessing a Value with `useContext`

To access the value of a context object in a child component, we use the `useContext()` hook. Here's an example:

```jsx
import { useContext } from "react";
function ChildComponent() {
  const myValue = useContext(MyContext);
  return <p>{myValue}</p>;
}
```

In this example, we use the `useContext()` hook to access the value of the `MyContext` context object.

## Benefits of `useContext`

Using `useContext` to pass data through the component tree in React has several benefits:

*   **Simpler code:** Using `useContext` can simplify code by removing the need to pass props down through multiple levels of components.
    
*   **Avoids prop drilling:** By using `useContext`, data can be accessed directly by child components without the need for intermediate components to pass the data down.
    
*   **Easier to manage state:** By using a context object to store state data, it is easier to manage state across multiple components without the need for complex state management libraries.
    
*   **Avoids naming conflicts:** `useContext` can help avoid naming conflicts by allowing components to access the values they need without having to worry about the names of the props.
    
*   **Improved performance:** `useContext` can improve performance by reducing the number of props that need to be passed down through multiple levels of components.

## Examples of `useContext`

### Example 1: Theming

One common use case for `useContext` is theming. In this example, we'll create a theme context that contains a color scheme and a component that uses the `useContext` hook to apply the theme.

```jsx
import React, { createContext, useContext } from "react";
const ThemeContext = createContext({ color: "blue" });
function App() {
  return (
    <ThemeContext.Provider value={{ color: "green" }}>
      {" "}
      <ThemedComponent />{" "}
    </ThemeContext.Provider>
  );
}
function ThemedComponent() {
  const { color } = useContext(ThemeContext);
  return (
    <div style={{ backgroundColor: color }}>
      {" "}
      <h1>Hello, World!</h1>{" "}
    </div>
  );
}
```

In this example, we create a `ThemeContext` object using `createContext()`. We then provide a value to the context using the `Provider` component in the `App` component. The `ThemedComponent` component uses the `useContext` hook to access the value provided by the `Provider` component and apply the appropriate styling.

### Example 2: Authentication

Another common use case for `useContext` is authentication. In this example, we'll create an authentication context that contains a user object and a component that uses the `useContext` hook to conditionally render content based on whether the user is logged in.

```jsx
import React, { createContext, useContext } from "react";
const AuthContext = createContext({ user: null });
function App() {
  const user = { name: "John" };
  return (
    <AuthContext.Provider value={{ user }}>
      {" "}
      <AuthenticatedContent />{" "}
    </AuthContext.Provider>
  );
}
function AuthenticatedContent() {
  const { user } = useContext(AuthContext);
  if (user) {
    return <p>Welcome, {user.name}!</p>;
  } else {
    return <p>Please log in to access content.</p>;
  }
}
```

In this example, we create an `AuthContext` object using `createContext()`. We then provide a value to the context using the `Provider` component in the `App` component. The `AuthenticatedContent` component uses the `useContext` hook to access the value provided by the `Provider` component and conditionally render content based on whether the user object exists.

These are just a couple of examples of how `useContext` can be used in React. The possibilities are endless, and it can be a powerful tool for simplifying your code and making it more maintainable.

## Exercises

1.  Create a context that contains a list of items and a component that displays the list using the `useContext` hook.
    
2.  Create a context that contains a function that increments a count and a component that uses the `useContext` hook to increment the count when a button is clicked.
    
3.  Create a context that contains a theme object with properties for `backgroundColor` and `textColor`, and a component that uses the `useContext` hook to apply the appropriate styling based on the theme.
    
4.  Create a context that contains a user object and a component that uses the `useContext` hook to conditionally render content based on whether the user is an admin.
    
5.  Create a context that contains an array of todos and a component that uses the `useContext` hook to display the todos in a list, with the ability to mark them as complete or delete them.
    

These exercises will help you practice using the `useContext` hook in different scenarios, and will give you a better understanding of how it can be used to simplify your code and make it more maintainable.