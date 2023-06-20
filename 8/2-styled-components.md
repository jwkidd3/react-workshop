# Session 8 - Part 2: Styled Components

Styled Components is a popular CSS-in-JS library that allows you to write CSS code directly inside your JavaScript code. It provides a convenient way to define and use reusable styled components in your React applications.

Styled Components uses tagged template literals to define styles for your components. Here's an example of how to use Styled Components to style a button component:

```jsx
import styled from "styled-components";
const Button = styled.button`
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 5px;

  &:hover {
      background-color: #3e8e41;
  }
`;
function App() {
  return (
    <div>
      {" "}
      <Button>Click Me</Button>{" "}
    </div>
  );
}
```

In this example, we use the `styled` function from the `styled-components` library to create a new styled component called `Button`. We then define the styles for this component using the tagged template literal syntax. The styles include a background color, border, padding, font size, and other CSS properties. We also define a hover effect for the button using the `&:hover` selector.

Using Styled Components, we can create reusable components with their own styles that can be easily reused across our application.

## Why Use Styled Components?

Styled Components offers several benefits for styling React components:

*   **Scoped Styles**: Each component has its own set of styles, which are scoped to that component only. This helps prevent style clashes and makes it easier to manage styles across your application.
    
*   **Reusable Components**: You can create reusable styled components that can be used across your application, reducing code duplication and making it easier to maintain your codebase.
    
*   **Dynamic Styling**: You can pass props to your styled components to dynamically change their styles based on the props.
    
*   **Easy to Test**: Because your styles are defined within your component code, it's easier to write unit tests for your components and ensure that they are rendering the correct styles.
    

Styled Components is just one of many CSS-in-JS libraries available for React, but it has gained popularity due to its ease of use and powerful features.

Sure, here's the second part with some real-world examples of how to use Styled Components:

## Examples

### 1\. Navigation Bar

A common use case for Styled Components is to create a navigation bar for your application. Here's an example of how you can create a simple navigation bar using Styled Components:

```jsx
import React from "react";
import styled from "styled-components";
const Navbar = styled.nav`
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #333;
  color: #fff;
  padding: 1rem;
`;
const NavItem = styled.a`
   color: #fff;
    margin: 0 1rem;
    text-decoration: none;

    &:hover {
        text-decoration: underline;
    }
`;
function App() {
  return (
    <Navbar>
      {" "}
      <h1>My App</h1>{" "}
      <div>
        {" "}
        <NavItem href="/">Home</NavItem> <NavItem href="/about">About</NavItem>{" "}
        <NavItem href="/contact">Contact</NavItem>{" "}
      </div>{" "}
    </Navbar>
  );
}

```

In this example, we create a `Navbar` styled component that defines the styles for the navigation bar. We also create a `NavItem` styled component that defines the styles for the navigation links. We use the `NavItem` component to create the links for the navigation bar.

### 2\. Card Component

Another use case for Styled Components is to create reusable UI components. Here's an example of how you can create a card component using Styled Components:

```jsx
import React from "react";
import styled from "styled-components";
const CardWrapper = styled.div`
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  padding: 1rem;
`;
const CardTitle = styled.h2`
  font-size: 1.5rem;
  margin: 0;
`;
const CardBody = styled.div`
  margin-top: 1rem;
`;
function Card({ title, children }) {
  return (
    <CardWrapper>
      {" "}
      <CardTitle>{title}</CardTitle> <CardBody>{children}</CardBody>{" "}
    </CardWrapper>
  );
}
function App() {
  return (
    <div>
      {" "}
      <Card title="My Card">
        {" "}
        <p>This is my card body.</p>{" "}
      </Card>{" "}
    </div>
  );
}
```

In this example, we create a `CardWrapper` styled component that defines the styles for the card component. We also create a `CardTitle` styled component and a `CardBody` styled component to define the styles for the title and body of the card. We use these components to create a reusable `Card` component that can be used throughout our application.

### 3\. Button Component

```jsx
import React from "react";
import styled from "styled-components";
const Button = styled.button`
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 5px;

  &:hover {
      background-color: #3e8e41;
  }
`;
function App() {
  return (
    <div>
      {" "}
      <Button>Click Me</Button> <Button disabled>Disabled Button</Button>{" "}
    </div>
  );
}

```

In this example, we create a `Button` styled component that defines the styles for a custom button component. We use the `Button` component to create two buttons: one that is enabled and one that is disabled. The `disabled` attribute is passed to the second button, and the `Button` component adjusts the styles accordingly.

### 4\. Input Component

Styled Components can also be used to create custom input components. Here's an example of how you can create a custom input component using Styled Components:

```jsx
import React from "react";
import styled from "styled-components";
const Input = styled.input`
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;

  &:focus {
    outline: none;
    border-color: #4CAF50;
    box-shadow: 0 0 5px #4CAF50;
  }
`;
function App() {
  return (
    <div>
      {" "}
      <label htmlFor="username">Username:</label>{" "}
      <Input type="text" id="username" name="username" />{" "}
      <label htmlFor="password">Password:</label>{" "}
      <Input type="password" id="password" name="password" />{" "}
    </div>
  );
}
```

In this example, we create an `Input` styled component that defines the styles for a custom input component. We use the `Input` component to create two input fields: one for a username and one for a password. When the input fields are focused, the `Input` component adjusts the styles to indicate that they are active.

```jsx
import React, { useState } from "react";
import styled, { keyframes } from "styled-components";
const pulse = keyframes`
from {
     transform: scale3d(1, 1, 1);
}
50% {
     transform: scale3d(1.05, 1.05, 1.05);
}
to {
     transform: scale3d(1, 1, 1);
}
`;
const Button = styled.button`
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 5px;
  animation: ${pulse} 1s ease-in-out infinite;

  &:hover {
      background-color: #3e8e41;
      animation: none;
  }
`;
function App() {
  const [clicks, setClicks] = useState(0);
  const handleClick = () => {
    setClicks(clicks + 1);
  };
  return (
    <div>
      {" "}
      <Button onClick={handleClick}>Click Me ({clicks})</Button>{" "}
    </div>
  );
}
```

In this example, we create a `Button` styled component that defines the styles for a custom button component. We also define a `pulse` keyframe animation using the `keyframes` helper function from Styled Components. We use the `Button` component to create a button that, when clicked, updates a counter that displays the number of clicks. The `Button` component applies the `pulse` animation to the button, causing it to animate with a pulsing effect. When the button is hovered over, the animation is turned off by setting the `animation` property to `none`.

Styled Components provide a powerful and flexible way to style React components, including the ability to define animations and apply them to components. By using Styled Components, you can create reusable and customizable components with a clean and readable syntax.

## Exercises

1.  Create a styled component for a `<Heading>` tag that applies a font size of `2rem` and a margin bottom of `1rem`.
2.  Create a styled component for a `<Link>` tag that applies a text decoration of `none` and a color of `blue`.
3.  Create a styled component for an `<Image>` tag that applies a border of `1px solid gray` and a border radius of `5px`.
4.  Create a styled component for a `<Container>` component that centers its content horizontally and vertically.
5.  Create a styled component for a `<Card>` component that applies a background color of `white`, a border of `1px solid #ccc`, a border radius of `5px`, and a box shadow of `0 0 10px rgba(0, 0, 0, 0.2)`.

Styled Components provide a powerful way to style React components. By using Styled Components, you can create reusable and customizable components with a clean and readable syntax. Take some time to practice creating your own styled components to get comfortable with this approach to styling in React.