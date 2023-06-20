# Session 4 - Part 4: JSX

## What is JSX?

JSX stands for JavaScript XML. It's a syntax extension for JavaScript that allows you to write HTML-like code in your JavaScript. JSX makes it easier to create and manipulate DOM elements in your React application.

Here's an example of how JSX can be used to create a simple `Hello World` component:

```javascript
import React from 'react';

function HelloWorld() {
  return (
    <div>
      <h1>Hello World!</h1>
    </div>
  );
}

export default HelloWorld;
```

In this example, the `HelloWorld` function returns a `div` element with an `h1` child element that contains the text "Hello World!". This JSX code is transpiled into regular JavaScript code that creates the DOM elements.

### Benefits of JSX

JSX has several benefits, including:

- It's easy to read and write. If you're familiar with HTML, you'll find JSX very similar.
- It allows for more efficient coding by enabling you to write HTML-like syntax instead of manually creating DOM elements with `document.createElement`.
- It enables you to easily incorporate JavaScript expressions and variables into your markup, making it easy to create dynamic and reusable components.

Here's an example of how to incorporate a JavaScript expression into JSX:

```javascript
import React from 'react';

function Greeting(props) {
  return (
    <div>
      <h1>Hello, {props.name}!</h1>
      <p>You are {props.age} years old.</p>
    </div>
  );
}

export default Greeting;
```

In this example, the `Greeting` component accepts `props` as an argument, and uses them to dynamically create the text inside the `h1` and `p` elements. This makes it easy to reuse the component with different `props` values.

### JSX vs HTML

It's important to note that JSX is not the same as HTML. JSX has a few key differences:

- JSX elements are not strings, but rather JavaScript expressions that are evaluated to produce React elements.
- In JSX, class is written as `className`, and for attributes like `onclick`, `onchange`, etc., you need to use camelCase, so `onClick`, `onChange`, etc.
- Style attributes are passed as objects instead of a string like in HTML. Here's an example:

  ```javascript
  const divStyle = {
    color: 'blue',
    backgroundColor: 'lightgray'
  };

  function MyComponent() {
    return (
      <div style={divStyle}>
        <h1>Hello World!</h1>
      </div>
    );
  }
  ```

  In this example, the `div` element has a `style` attribute that's passed as an object with properties for `color` and `backgroundColor`.

Overall, JSX is a powerful tool that makes it easier to create and manipulate DOM elements in your React application.
