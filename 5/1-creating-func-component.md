# Session 5 - Part 1: Creating Functional Components

React functional components are a simpler way of creating React components. They are just functions that return React elements, and they don't have any lifecycle methods or state.

## Creating a Functional Component

To create a functional component, you can define a function that returns a React element. Here's an example:

```js
function MyComponent() {
  return <div>Hello, world!</div>;
}
```

In this example, we define a function called `MyComponent` that returns a div element with the text "Hello, world!".

## Using a Functional Component

Once you've created a functional component, you can use it just like any other React component. You can import it into another file and use it in your JSX code.

Here's an example of how to use the `MyComponent` component we defined earlier:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import MyComponent from './MyComponent';

ReactDOM.render(<MyComponent />, document.getElementById('root'));
```

In this example, we import the `MyComponent` component and render it inside the `ReactDOM.render` method.

## Props in Functional Components

Functional components can also receive props, just like class components. You can access the props inside the function using the function's parameters.

Here's an example of a functional component that receives a `name` prop:

```js
function Greeting(props) {
  return <div>Hello, {props.name}!</div>;
}
```

In this example, we define a function called `Greeting` that receives a `name` prop and returns a div element that uses the `name` prop to render the text "Hello, {props.name}!".

## Exercises

1. Create a functional component that renders a button with the text "Click me!".

<details>
  <summary>Answer</summary>

 ```jsx

    function Button() {
      return <button>Click me!</button>;
    }

  ```
</details>

2. Create a functional component that receives a `color` prop and renders a div element with the background color set to the value of the `color` prop.

<details>
  <summary>Answer</summary>

 ```jsx

    function ColoredDiv(props) {
      return (<div style={{ backgroundColor: props.color}}>Colored div</div>);
    }

  ```
</details>

3. Create a functional component that receives a `title` and `subtitle` prop and renders a div element with the `title` prop as the main text and the `subtitle` prop as the subtext.

<details>
  <summary>Answer</summary>

 ```jsx

    function TitleSubtitle(props) {
      return (
        <div>
          <h1>{props.title}</h1>
          <h2>{props.subtitle}</h2>
        </div>
      );
    }

  ```
</details>

4. Create a functional component that receives a `name` and `age` prop and renders a div element with the `name` prop as the main text and the `age` prop as the subtext.

<details>
  <summary>Answer</summary>

 ```jsx

    function NameAge(props) {
      return (
        <div>
          <h1>{props.name}</h1>
          <h2>{props.age}</h2>
        </div>
      );
    }

  ```
</details>
