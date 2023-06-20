# Session 9 - Part 2: Handling Form Data

Handling form data in React involves capturing user input and updating the component's state based on the input. There are two main approaches to handling form data in React: controlled components and uncontrolled components.

In a controlled component, the component manages its own state and updates its own values based on user input. The component uses the `onChange` event to update its state and the `value` prop to control the value of the input element.

In an uncontrolled component, the component does not manage its own state and instead relies on the DOM to keep track of the value of the input element. The value of the input element can be retrieved using the `useRef` hook and the `ref` prop.

Both approaches have their own trade-offs and the choice between the two depends on the specific requirements of the form and the application.

It's also important to note that React provides support for form validation and error handling. This allows you to validate user input and provide feedback to the user if there are any errors in their input.

## Examples:

Controlled Component Example:

```jsx
const ControlledForm = () => {
  const [username, setUsername] = React.useState("");
  const [password, setPassword] = React.useState("");
  const handleSubmit = (event) => {
    event.preventDefault();
    console.log(`Username: ${username} Password: ${password}`);
  };
  const handleUsernameChange = (event) => {
    setUsername(event.target.value);
  };
  const handlePasswordChange = (event) => {
    setPassword(event.target.value);
  };
  return (
    <form onSubmit={handleSubmit}>
      {" "}
      <div>
        {" "}
        <label htmlFor="username">Username:</label>{" "}
        <input
          type="text"
          id="username"
          value={username}
          onChange={handleUsernameChange}
        />{" "}
      </div>{" "}
      <div>
        {" "}
        <label htmlFor="password">Password:</label>{" "}
        <input
          type="password"
          id="password"
          value={password}
          onChange={handlePasswordChange}
        />{" "}
      </div>{" "}
      <button type="submit">Submit</button>{" "}
    </form>
  );
};

```

In this example, the `ControlledForm` component manages its own state using the `useState` hook. The component updates its state based on user input using the `onChange` event and the `setUsername` and `setPassword` functions. The component also has a `handleSubmit` function that logs the values of `username` and `password` to the console when the form is submitted.

Uncontrolled Component Example:

``const UncontrolledForm = () => {   const usernameRef = React.useRef();   const passwordRef = React.useRef();    const handleSubmit = (event) => {     event.preventDefault();     console.log(`Username: ${usernameRef.current.value} Password: ${passwordRef.current.value}`);   };    return (     <form onSubmit={handleSubmit}>       <div>         <label htmlFor="username">Username:</label>         <input type="text" id="username" ref={usernameRef} />       </div>       <div>         <label htmlFor="password">Password:</label>         <input type="password" id="password" ref={passwordRef} />       </div>       <button type="submit">Submit</button>     </form>   ); };``

In this example, the `UncontrolledForm` component does not manage its own state and instead relies on the DOM to keep track of the values of the input elements. The component uses the `useRef` hook to create references to the input elements and the `ref` prop to assign the references to the elements. The component also has a `handleSubmit` function that logs the values of the input elements to the console when the form is submitted. The values of the input elements are accessed using the `current` property of the refs.

## Exercises:

1.  Create a controlled form component that takes a list of form fields as a prop and dynamically generates the form based on the fields.
    
2.  Create an uncontrolled form component that takes a list of form fields as a prop and dynamically generates the form based on the fields. Retrieve the values of the form fields using `useRef`.
    
3.  Add form validation to both the controlled and uncontrolled form components. Display error messages next to each form field if the field is invalid.
    
4.  Add support for select and checkbox form fields to both the controlled and uncontrolled form components.
    
5.  Compare the code required to create a controlled form vs an uncontrolled form. Consider the trade-off between the two approaches and when you would choose to use one over the other.
    

These exercises will give you hands-on experience with handling form data in React and help you understand the trade-off between the two approaches.