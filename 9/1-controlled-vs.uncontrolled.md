# Session 9 - Part 1: Controlled vs Uncontrolled Components

In React, components can be classified into two types: controlled components and uncontrolled components. These terms refer to the way in which a component manages and updates its state.

A controlled component is one where React is responsible for managing the component's state. This means that the component's state is updated via props passed down from its parent component. Whenever the user interacts with the component, such as entering text into an input field, React updates the component's state and re-renders the component with the new state.

On the other hand, an uncontrolled component is one where the component manages its own state internally. In this case, the component's state is not managed by React, but rather by the component itself. Whenever the user interacts with the component, such as entering text into an input field, the component updates its own state and re-renders itself with the new state.

The main difference between these two types of components is where the state is managed. With a controlled component, the state is managed by React, while with an uncontrolled component, the state is managed by the component itself.

Knowing the difference between controlled and uncontrolled components is important when working with forms in React, as it affects how you handle form input and how you retrieve the input data from the form. Depending on your needs, you may choose to use controlled components, uncontrolled components, or a combination of both.

In the next section, I will provide some examples to illustrate the differences between controlled and uncontrolled components.

## Examples

### Examples of Controlled Components:

```jsx
const ControlledInput = () => {
  const [value, setValue] = React.useState("");
  const handleChange = (event) => {
    setValue(event.target.value);
  };
  return <input type="text" value={value} onChange={handleChange} />;
};
const ControlledSelect = () => {
  const [selectedOption, setSelectedOption] = React.useState("option1");
  const handleChange = (event) => {
    setSelectedOption(event.target.value);
  };
  return (
    <select value={selectedOption} onChange={handleChange}>
      {" "}
      <option value="option1">Option 1</option>{" "}
      <option value="option2">Option 2</option>{" "}
      <option value="option3">Option 3</option>{" "}
    </select>
  );
```

In these examples, the `ControlledInput` and `ControlledSelect` functional components manage their own state and update their own values based on user input. The components use the `onChange` event to update their state and the `value` prop to control the value of the input and select elements.

### Examples of Uncontrolled Components:

```jsx
const UncontrolledInput = () => {
  return <input type="text" />;
};
const UncontrolledSelect = () => {
  return (
    <select>
      {" "}
      <option value="option1">Option 1</option>{" "}
      <option value="option2">Option 2</option>{" "}
      <option value="option3">Option 3</option>{" "}
    </select>
  );
};
```

In these examples, the `UncontrolledInput` and `UncontrolledSelect` functional components do not manage their own state and instead rely on the DOM to keep track of their value. These components are simpler to write, but provide less control over the behavior of the component.

### Examples of Controlled Components:

```jsx
const ControlledInput = () => {
  const [value, setValue] = React.useState("");
  const handleChange = (event) => {
    setValue(event.target.value);
  };
  return <input type="text" value={value} onChange={handleChange} />;
};
const ControlledSelect = () => {
  const [selectedOption, setSelectedOption] = React.useState("option1");
  const handleChange = (event) => {
    setSelectedOption(event.target.value);
  };
  return (
    <select value={selectedOption} onChange={handleChange}>
      {" "}
      <option value="option1">Option 1</option>{" "}
      <option value="option2">Option 2</option>{" "}
      <option value="option3">Option 3</option>{" "}
    </select>
  );
};

```

In these examples, the `ControlledInput` and `ControlledSelect` functional components manage their own state and update their own values based on user input. The components use the `onChange` event to update their state and the `value` prop to control the value of the input and select elements.

### Examples of Uncontrolled Components and Retrieving the Value using `useRef`:

```jsx
const UncontrolledInput = () => {
  const inputRef = React.useRef();
  const handleSubmit = (event) => {
    event.preventDefault();
    console.log(inputRef.current.value);
  };
  return (
    <form onSubmit={handleSubmit}>
      {" "}
      <input type="text" ref={inputRef} /> <button type="submit">Submit</button>{" "}
    </form>
  );
};
const UncontrolledSelect = () => {
  const selectRef = React.useRef();
  const handleSubmit = (event) => {
    event.preventDefault();
    console.log(selectRef.current.value);
  };
  return (
    <form onSubmit={handleSubmit}>
      {" "}
      <select ref={selectRef}>
        {" "}
        <option value="option1">Option 1</option>{" "}
        <option value="option2">Option 2</option>{" "}
        <option value="option3">Option 3</option>{" "}
      </select>{" "}
      <button type="submit">Submit</button>{" "}
    </form>
  );
};
```

In these examples, the `UncontrolledInput` and `UncontrolledSelect` functional components do not manage their own state and instead rely on the DOM to keep track of their value. To retrieve the value of the uncontrolled components, the `useRef` hook is used to create a reference to the input and select elements. The `ref` prop is then used to assign the reference to the elements. The value of the uncontrolled components can then be accessed and logged to the console using the `current` property of the ref.

## Exercises:

1.  Create a controlled input component that takes an initial value as a prop and updates its own state based on user input.
    
2.  Create an uncontrolled input component and retrieve its value using `useRef`. Log the value to the console when a form submit button is clicked.
    
3.  Create a controlled select component that takes an initial selected option as a prop and updates its own state based on the selected option.
    
4.  Create an uncontrolled select component and retrieve its value using `useRef`. Log the value to the console when a form submit button is clicked.
    
5.  Compare the code required to create a controlled input vs an uncontrolled input, and a controlled select vs an uncontrolled select. Consider the trade-off between the two approaches and when you would choose to use one over the other.
    

These exercises will give you hands-on experience with the controlled and uncontrolled components in React and help you understand the trade-off between the two approaches.