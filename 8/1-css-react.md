# Session 8 - Part 1: Using CSS with React

React provides several ways to style your components, including inline styles and importing a normal CSS file. Each of these approaches has its own strengths and weaknesses, so it's important to understand the trade-offs before choosing one.

## Inline Styles

React allows you to add styles directly to your components using the `style` prop. This prop accepts an object with CSS property-value pairs. Here's an example:

```jsx
function MyComponent() {
  const styles = {
    backgroundColor: "blue",
    color: "white",
    padding: "10px",
    borderRadius: "5px",
  };
  return <div style={styles}>Hello, World!</div>;
}
```

In this example, we define a `styles` object with several CSS properties, and then pass this object to the `style` prop of a `div` element.

Before React, inline styles were commonly used in traditional HTML pages. For example:

```html
<div style="background-color: blue; color: white; padding: 10px; border-radius: 5px;">
  Hello, World!
</div>;

```

While inline styles can be convenient, they can also make it difficult to reuse styles across components and can clutter your JSX code.

## Importing a Normal CSS File

Another way to style your components in React is by importing a normal CSS file. You can use the `import` statement to import a CSS file into your component, and then apply the styles using the `className` prop. Here's an example:

```css
/* styles.css */
 .myClass {
     background-color: blue;
     color: white;
     padding: 10px;
     border-radius: 5px;
}
```

```jsx
import "./styles.css";
function MyComponent() {
  return <div className="myClass">Hello, World!</div>;
}
```

In this example, we define a CSS class called `myClass` in a separate CSS file called `styles.css`. We then import this file into our component using the `import` statement and apply the `myClass` class to our `div` element using the `className` prop. It's important to note that in JSX, you should use `className` instead of `class` to apply CSS classes to elements, as `class` is a reserved keyword in JavaScript.

## Using CSS with React

### Examples

#### Inline Styles

Using inline styles in React allows you to apply CSS directly to your components. Here are a few examples of how you can use inline styles:

1.  Creating a progress bar:
    
    ```jsx
        function ProgressBar({ value, max }) {
            const percent = (value / max) * 100;
            const styles = {
                backgroundColor: "#f5f5f5",
                borderRadius: "5px",
                height: "10px",
                position: "relative",
            };
            const fillStyles = {
                backgroundColor: "#4CAF50",
                borderRadius: "5px",
                height: "100%",
                left: "0",
                position: "absolute",
                top: "0",
                transition: "width 0.5s ease-in-out",
                width: `${percent}%`,
            };
            return (
                <div style={styles}>
                {" "}
                <div style={fillStyles}></div>{" "}
                </div>
            );
        }
    ```
    
    In this example, we define two objects for our `styles` and `fillStyles`. The `styles` object defines the base styles for the progress bar, while the `fillStyles` object defines the styles for the progress bar's fill, which is adjusted based on the `value` and `max` props.
    
2.  Creating a custom checkbox:
    
    ```jsx
        function Checkbox({ checked, onChange }) {
            const styles = {
                appearance: "none",
                backgroundColor: "#fafafa",
                border: "1px solid #ccc",
                borderRadius: "50%",
                cursor: "pointer",
                height: "18px",
                position: "relative",
                width: "18px",
            };
            const checkmarkStyles = {
                backgroundColor: "#4CAF50",
                borderRadius: "50%",
                height: "10px",
                left: "50%",
                position: "absolute",
                top: "50%",
                transform: "translate(-50%, -50%)",
                transition: "background-color 0.2s ease-in-out",
                width: "10px",
                opacity: checked ? "1" : "0",
            };
            return (
                <label>
                {" "}
                <input
                    type="checkbox"
                    checked={checked}
                    onChange={onChange}
                    style={{ display: "none" }}
                />{" "}
                <span style={styles}>
                    {" "}
                    <span style={checkmarkStyles}></span>{" "}
                </span>{" "}
                </label>
            );
        }
    ```
    
    In this example, we define two objects for our `styles` and `checkmarkStyles`. The `styles` object defines the base styles for the checkbox, while the `checkmarkStyles` object defines the styles for the checkbox's checkmark, which is adjusted based on the `checked` prop.


#### Importing a Normal CSS File

Another way to style your React components is by importing a normal CSS file using the `import` statement. Here are a few examples of how you can use imported CSS files:

1.  Creating a card component:
    
    ```css
        /* styles.css */
        .card {
            background-color: #fff;
            border-radius: 5px;
            box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
            padding: 20px;
            width: 300px;
        }
        .card-title {
            font-size: 20px;
            margin-bottom: 10px;
        }
        .card-text {
            font-size: 14px;
            color: #666;
        }
    ```
    
    ```jsx
        import "./styles.css";
        function Card() {
            return (
                <div className="card">
                {" "}
                <h2 className="card-title">Card Title</h2>{" "}
                <p className="card-text">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                </p>{" "}
                </div>
            );
        }
    ```
    
    In this example, we define a CSS file called `styles.css` that contains styles for a card component. We then import this file into our component using the `import` statement and apply the appropriate classes to our `h2` and `p` elements using the `className` prop.
    
2.  Styling a button component:
    
    ```css
        /* styles.css */
        .button {
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
        }
        .button:hover {
            background-color: #3e8e41;
        }
    ```
    
    ```jsx
        import "./styles.css";
        function Button({ text }) {
            return <button className="button">{text}</button>;
        }
    ```
    
    In this example, we define a CSS file called `styles.css` that contains styles for a button component. We then import this file into our component using the `import` statement and apply the `.button` class to our `button` element using the `className` prop. We also define a hover effect for the button by adding the `.button:hover` class to our CSS file.
    

### Best Practices

When using CSS with React, there are a few best practices to keep in mind:

*   Use the `className` prop instead of the `class` attribute to apply CSS classes to your elements.
*   Avoid using inline styles for complex styling, as they can quickly become hard to manage.
*   Consider using CSS modules or CSS-in-JS libraries like styled-components or Emotion for more complex styling needs.

By following these best practices, you can write clean, maintainable CSS code for your React components.

## Exercises

1.  Create a component that displays a list of items, with each item containing an image, a title, and a description. Style the list and each item using CSS.
    
2.  Create a component that displays a form with input fields for a name, email, and message. Style the form and the input fields using CSS.
    
3.  Create a component that displays a navbar with links to different pages of your website. Style the navbar and the links using CSS.
    
4.  Create a component that displays a banner with a call-to-action button. Style the banner and the button using CSS.
    

These exercises will help you get familiar with applying CSS styles to React components and improve your overall proficiency in React development.