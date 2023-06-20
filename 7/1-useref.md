# Session 7 - Part 1: useRef Hook

The `useRef` hook in React provides a way to store mutable values that persist between renders without causing a re-render. It is similar to instance variables in class components.

## How to use `useRef`

The `useRef` hook can be used to create a mutable reference that persists between renders of a component. Here's an example:

```jsx
import { useRef } from "react";
function FormComponent() {
  const nameRef = useRef(null);
  const emailRef = useRef(null);
  const handleSubmit = (event) => {
    event.preventDefault();
    const formData = {
      name: nameRef.current.value,
      email: emailRef.current.value,
    };
    console.log(formData); // Submit the form data to a server
  };
  return (
    <form onSubmit={handleSubmit}>
      {" "}
      <div>
        {" "}
        <label htmlFor="name">Name:</label>{" "}
        <input type="text" id="name" ref={nameRef} />{" "}
      </div>{" "}
      <div>
        {" "}
        <label htmlFor="email">Email:</label>{" "}
        <input type="email" id="email" ref={emailRef} />{" "}
      </div>{" "}
      <button type="submit">Submit</button>{" "}
    </form>
  );
}
```

In this example, the `useRef` hook is used to create mutable references to the form input elements. The `handleSubmit` function uses the `current` properties of the `nameRef` and `emailRef` to retrieve the values of the form inputs. The form data is then logged to the console and submitted to a server. Since the use of `useRef` does not trigger a re-render, this technique is useful for persisting form data across renders.