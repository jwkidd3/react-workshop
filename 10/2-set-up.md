# Session 10 - Part 2: Setting up React-Router

React Router is a library that allows us to handle client-side routing in our React applications. It is not included in the React library by default, so we need to install and set it up separately.

## Step 1: Install React Router

To get started, we need to install `react-router-dom`, which is a collection of routing components for React.

Open your terminal and run the following command:

```bash
npm install react-router-dom
```

## Step 2: Import BrowserRouter

We need to import the `BrowserRouter` component from `react-router-dom` and wrap our app component with it. This component uses the HTML5 history API to keep the UI in sync with the URL.

In `index.js`:

```jsx
import React from "react";
import ReactDOM from "react-dom";
import { BrowserRouter } from "react-router-dom";
import App from "./App";
ReactDOM.render(
  <BrowserRouter>
    {" "}
    <App />{" "}
  </BrowserRouter>,
  document.getElementById("root")
);

```

## Step 3: Create Routes

Now we can start creating routes for our application. A route is simply a mapping between a URL and a component.

We can define routes using the `Route` component from `react-router-dom`. The `Route` component has two required props: `path` and `component`. The `path` prop specifies the URL that should match the route, and the `component` prop specifies the component that should be rendered when the URL matches.

In `App.js`:

```jsx
import React from "react";
import { Route } from "react-router-dom";
import HomePage from "./HomePage";
import AboutPage from "./AboutPage";
function App() {
  return (
    <div>
      {" "}
      <Route path="/" exact component={HomePage} />{" "}
      <Route path="/about" component={AboutPage} />{" "}
    </div>
  );
}
export default App;
```

In this example, we have created two routes. The first route will match the root URL ("/") and render the `HomePage` component. The second route will match the "/about" URL and render the `AboutPage` component.

Note that we are wrapping the `Route` components in a `div` element. This is because React requires that we wrap multiple elements in a single parent element.

## Step 4: Add Navigation

To navigate between routes, we need to create links using the `Link` component from `react-router-dom`.

In `Header.js`:

```jsx
import React from "react";
import { Link } from "react-router-dom";
function Header() {
  return (
    <nav>
      {" "}
      <ul>
        {" "}
        <li>
          {" "}
          <Link to="/">Home</Link>{" "}
        </li>{" "}
        <li>
          {" "}
          <Link to="/about">About</Link>{" "}
        </li>{" "}
      </ul>{" "}
    </nav>
  );
}
export default Header;
```

In this example, we have created two links using the `Link` component. The `to` prop specifies the URL that the link should navigate to.

## Step 5: Test the Application

That's it! We have now set up client-side routing using React Router.

Start your application by running `npm start` and test the navigation by clicking on the links.

```bash
npm start
```