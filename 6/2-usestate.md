# Session 6 - Part 2: useState Hook

The `useState` hook is used to add state to functional components. It takes an initial state value as an argument and returns an array with two elements: the current state value and a function to update the state value.

The syntax for using `useState` looks like this:

```jsx
import React, { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

In the example above, we are using the `useState` hook to initialize a state variable called `count` with an initial value of `0`. We then render the current value of `count` in a `p` tag, along with a button that updates the state value when clicked.

Here is another example that uses `useState` to toggle the visibility of an element:

```jsx
import React, { useState } from 'react';

function Example() {
  const [visible, setVisible] = useState(true);

  return (
    <div>
      <button onClick={() => setVisible(!visible)}>
        {visible ? 'Hide' : 'Show'}
      </button>
      {visible && <p>This text is only visible when the button is clicked.</p>}
    </div>
  );
}
```

In this example, we use `useState` to initialize a state variable called `visible` with an initial value of `true`. We then render a button that toggles the value of `visible` when clicked. Finally, we conditionally render a paragraph tag based on the value of `visible`.

## Exercises

1. Create a new functional component called `ColorPicker` that uses `useState` to maintain a state variable called `color` with an initial value of `"red"`. Render a `div` with a background color of `color` and a button that updates the `color` state value to `"blue"` when clicked.

2. Create a new functional component called `TemperatureConverter` that uses `useState` to maintain a state variable called `celsius` with an initial value of `0`. Render two `input` fields, one for celsius and one for fahrenheit. When the value of one input changes, update the other input's value to the converted temperature.

3. Create a new functional component called `RandomNumber` that uses `useState` to maintain a state variable called `number` with an initial value of `0`. Render a `div` with the current value of `number` and two buttons, one that increments the number by 1 and one that decrements the number by 1.
