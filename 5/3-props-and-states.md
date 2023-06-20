# Session 5 - Part 3: Props and State

## Props

- Props are read-only, meaning you can't change their values inside the component. You can think of them as function arguments.

- You can pass any data type as a prop, including strings, numbers, arrays, objects, and even other components.

- To pass props to a component, you simply add them as attributes in the JSX when rendering the component.

- In the component definition, you can access the props as a parameter to the function.

Example:

```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return (
    <div>
      <Greeting name="John" />
      <Greeting name="Jane" />
    </div>
  );
}
```

## State

- State is mutable, meaning you can change its values inside the component. You can think of it as a private data store for the component.

- You should initialize state in the constructor method of the component.

- You can update state using the `setState()` method, which is asynchronous and merges the changes into the existing state.

- Changes to state trigger a re-render of the component, so you can see the updated values.

Example:

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  incrementCount() {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.incrementCount()}>Increment</button>
      </div>
    );
  }
}
```
