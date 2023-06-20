# Session 9 - Part 3: Form Validation

Form validation is an important aspect of creating user-friendly forms. In React, form validation can be implemented using either controlled components or uncontrolled components. The main goal of form validation is to ensure that user input is in the correct format and meets certain criteria before it is submitted to the server.

React provides support for form validation through the use of custom validation functions. These functions can be used to validate individual form fields, or to validate the entire form. The validation functions can be called in response to user input, such as when a form field changes, or when the form is submitted.

In addition to validating user input, form validation also involves providing feedback to the user in the form of error messages. Error messages can be displayed next to individual form fields, or at the top of the form.

It's important to note that form validation should be handled both on the client-side and on the server-side. Client-side validation provides quick feedback to the user and reduces the amount of data sent to the server, while server-side validation ensures that the data is secure and meets the required criteria.

Certainly, here's the second part of the explanation of Form Validation in React, including examples:

## Examples:

Here's an example of a controlled form component with basic email validation:

```jsx
const ControlledFormWithValidation = () => {
  const [email, setEmail] = React.useState("");
  const [error, setError] = React.useState(null);
  const handleSubmit = (event) => {
    event.preventDefault();
    if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
      setError("Invalid email address");
    } else {
      setError(null);
      console.log(`Email: ${email}`);
    }
  };
  const handleEmailChange = (event) => {
    setEmail(event.target.value);
  };
  return (
    <form onSubmit={handleSubmit}>
      {" "}
      <div>
        {" "}
        <label htmlFor="email">Email:</label>{" "}
        <input
          type="email"
          id="email"
          value={email}
          onChange={handleEmailChange}
        />{" "}
      </div>{" "}
      {error && <div style={{ color: "red" }}>{error}</div>}{" "}
      <button type="submit">Submit</button>{" "}
    </form>
  );
};
```

In this example, the `ControlledFormWithValidation` component manages its own state using the `useState` hook. The component updates its state based on user input using the `onChange` event and the `setEmail` function. The component also has a `handleSubmit` function that performs email validation and logs the value of `email` to the console if the email address is valid. If the email address is invalid, an error message is displayed to the user.

Here's an example of an uncontrolled form component with basic email validation:

```jsx
const UncontrolledFormWithValidation = () => {
  const emailRef = React.useRef();
  const [error, setError] = React.useState(null);
  const handleSubmit = (event) => {
    event.preventDefault();
    const email = emailRef.current.value;
    if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
      setError("Invalid email address");
    } else {
      setError(null);
      console.log(`Email: ${email}`);
    }
  };
  return (
    <form onSubmit={handleSubmit}>
      {" "}
      <div>
        {" "}
        <label htmlFor="email">Email:</label>{" "}
        <input type="email" id="email" ref={emailRef} />{" "}
      </div>{" "}
      {error && <div style={{ color: "red" }}>{error}</div>}{" "}
      <button type="submit">Submit</button>{" "}
    </form>
  );
};
```

In this example, the `UncontrolledFormWithValidation` component does not manage its own state and instead relies on the DOM to keep track of the value of the email input element. The component uses the `useRef` hook to create a reference to the email input element and the `ref` prop to assign the reference to the input element. The component then retrieves the value of the email input element in the `handleSubmit` function by accessing the `value` property of the `emailRef.current` object. The rest of the form validation logic is the same as in the controlled form example.

It's important to understand that both controlled and uncontrolled forms have their own advantages and disadvantages. Controlled forms provide better control over the state of the form and make it easier to implement form validation, while uncontrolled forms are easier to implement and provide better performance in certain cases. The choice between controlled and uncontrolled forms depends on the specific requirements of the form and the application.

In general, it's recommended to use controlled forms for forms that require complex validation or that need to be integrated with other parts of the application, while uncontrolled forms are a good choice for simple forms that don't require complex validation.

## Exercises:

1.  Create a controlled form component with multiple fields and implement form validation for all the fields.
    
2.  Create an uncontrolled form component with multiple fields and implement form validation for all the fields. Retrieve the values of the form fields using `useRef`.
    
3.  Add form validation for different types of form fields, such as text fields, number fields, select fields, and checkbox fields.
    
4.  Display error messages next to individual form fields for each validation error.
    
5.  Compare the code required to validate a controlled form vs an uncontrolled form. Consider the trade-off between the two approaches and when you would choose to use one over the other.
    

These exercises will give you hands-on experience with implementing form validation in React and help you understand the trade-off between the two approaches.