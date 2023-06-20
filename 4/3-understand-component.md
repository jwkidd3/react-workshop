# Session 4 - Part 3: Understanding Components

At the heart of React are components. Components are the building blocks of React applications, and they allow you to create reusable pieces of user interface (UI) that can be composed together to create more complex interfaces.

## What is a Component?

In React, a component is a function or class that returns a React element. A React element is a lightweight description of what you want to see on the screen, and it's typically written using JSX.

Here's an example of a simple React component:

```js
function Greeting(props) {
  return (<h1>Hello, {props.name}!</h1>);
}
```

This component is called "Greeting", and it takes a single prop called "name". The component returns a `<h1>` element that says "Hello, {props.name}!", where {props.name} is replaced with the value of the "name" prop.

## Function Components vs. Class Components

There are two types of components in React: function components and class components.

Function components are the simpler of the two, and they're just JavaScript functions that return a React element. Here's an example:

```jsx
function Greeting(props) {
  return (<h1>Hello, {props.name}!</h1>);
}
```

Class components are a bit more complex, but they offer some additional features like local state and lifecycle methods. Here's an example of a class component:

```jsx
class Greeting extends React.Component {
  render() {
    return (<h1>Hello, {this.props.name}!</h1>);
  }
}
```

This class component is also called "Greeting", and it has a single prop called "name". The component's render method returns a `<h1>` element that says "Hello, {this.props.name}!", where {this.props.name} is replaced with the value of the "name" prop.

## Composing Components

One of the key benefits of React components is that they're composable. This means that you can take multiple components and combine them to create more complex components.

For example, let's say you have a component called "Header" that displays the title of your application, and another component called "Navigation" that displays a list of links. You could combine these two components to create a "HeaderWithNavigation" component that displays both the title and the navigation links.

Here's an example of how you might define the "Header" and "Navigation" components:

```jsx
function Header(props) {
  return <h1>{props.title}</h1>;
}

function Navigation(props) {
  return (
    <ul>
      <li><a href="#">Link 1</a></li>
      <li><a href="#">Link 2</a></li>
      <li><a href="#">Link 3</a></li>
    </ul>
  );
}
```

And here's an example of how you might compose these two components to create a "HeaderWithNavigation" component:

```jsx
function HeaderWithNavigation(props) {
  return (
    <div>
      <Header title={props.title} />
      <Navigation />
    </div>
  );
}
```

This "HeaderWithNavigation" component renders a `<div>` element that contains a "Header" component and a "Navigation" component.
