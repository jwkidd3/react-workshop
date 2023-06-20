# Session 5 - Part 2: Rendering Components

Let's proceed to the next part which is Rendering Components.

## JSX in Depth

We've already covered JSX, but let's dive a little deeper into it.

In JSX, you can embed any JavaScript expression by wrapping it in curly braces, {}, like so:

```jsx
const name = "John Doe";
const element = <h1>Hello, {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById("root")
);
```

You can even include arrays of elements:

```jsx
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => (
  <li key={number.toString()}>{number}</li>
));

ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById("root")
);
```

And you can use ternary operators for conditional rendering:

```js
const isLoggedIn = true;

ReactDOM.render(
  <div>{isLoggedIn ? "Welcome!" : "Please log in"}</div>,
  document.getElementById("root")
);
```

## Rendering Elements

In React, elements are the smallest building blocks of a React application. An element describes what you want to see on the screen. 

React elements are immutable. Once you create an element, you can't change its children or attributes. Instead, you create a new element and replace the old one.

To render a React element into a root DOM node, pass both to `ReactDOM.render()`:

```jsx
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById("root"));
```

This will render the element into a div with the ID of "root" in your HTML file.

### Rendering Components

Components are reusable pieces of UI. A component is a function or a class that returns a React element. They can take in props, which are like function arguments.

Here is an example of a functional component:

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="John" />;

ReactDOM.render(element, document.getElementById("root"));
```

And here is an example of a class component:

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

const element = <Welcome name="John" />;

ReactDOM.render(element, document.getElementById("root"));
```

Both of these examples will render a "Hello, John" heading to the page.

## Exercises

1. Create a new functional component called `Greeting` that takes in a `name` prop and returns a greeting message, like "Hello, John".

<details>
  <summary>Answer</summary>

```jsx
import React from 'react';

function Greeting({ name }) {
  return (
    <div>
      Hello, {name}
    </div>
  );
}

export default Greeting;

```
</details>


2. Create a class component called `Counter` that has a `count` state and a button that increments the count when clicked.

<details>
  <summary>Answer</summary>
  
```jsx
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);

    this.state = {
      count: 0
    };

    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState((prevState) => ({ count: prevState.count + 1 }));
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.handleClick}>Increment</button>
      </div>
    );
  }
}

export default Counter;

```
</details>


3. Create a class component called `Person` that has `name`, `age`, and `gender` props and displays them in a sentence, like "John is a 35-year-old male".

<details>
  <summary>Answer</summary>
  
```jsx
import React from 'react';

function Person({ name, age, gender }) {
  return (
    <div>
      {name} is a {age}-year-old {gender}
    </div>
  );
}

export default Person;

```
</details>
