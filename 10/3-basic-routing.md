# Session 10 - Part 3: Routing Basics

Routing is the process of matching a URL to a specific component in your React application. In other words, it allows you to define which component should be rendered based on the current URL path.

React Router is a third-party library that allows you to add routing functionality to your React applications. It provides a declarative way to handle routing and makes it easy to manage your application's state and UI based on the URL.

## BrowserRouter

The `BrowserRouter` component is a wrapper around your entire application that enables client-side routing. It should be added to your root component.

Here is an example:

```jsx
import { BrowserRouter } from "react-router-dom";
import Home from "./components/Home";
import About from "./components/About";
function App() {
  return (
    <BrowserRouter>
      {" "}
      <Switch>
        {" "}
        <Route path="/about">
          {" "}
          <About />{" "}
        </Route>{" "}
        <Route path="/">
          {" "}
          <Home />{" "}
        </Route>{" "}
      </Switch>{" "}
    </BrowserRouter>
  );
}
```

In this example, we have imported the `BrowserRouter` component from the `react-router-dom` package and wrapped our entire application inside it. We have also defined two routes using the `Route` component. The `path` prop defines the URL path that should match this route and the component that should be rendered when the route matches is passed as a child.

## Switch

The `Switch` component is used to group `Route` components together. It ensures that only one of the defined routes is rendered at a time. This is important because if you have multiple routes that match the current URL path, all of them will be rendered if they are not wrapped in a `Switch`.

## Route

The `Route` component defines a mapping between a URL path and a component that should be rendered when the path is matched. It can be used in combination with the `Switch` component to define different routes.

Here is an example:

```jsx
import { Route } from "react-router-dom";
import Home from "./components/Home";
function App() {
  return (
    <div>
      {" "}
      <h1>Welcome to my App!</h1>{" "}
      <Route path="/">
        {" "}
        <Home />{" "}
      </Route>{" "}
    </div>
  );
}
```

In this example, we have imported the `Route` component from the `react-router-dom` package and defined a single route for the home page. The `path` prop defines the URL path that should match this route and the `Home` component is rendered when the route matches.

## Link

The `Link` component is used to create links between different pages in your application. It generates an `<a>` element that can be clicked to navigate to the specified URL.

Here is an example:

```jsx
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
```

In this example, we have imported the `Link` component from the `react-router-dom` package and used it to create links to the home and about pages of our application.

Overall, React Router provides a powerful and flexible way to handle routing in your React applications. With its intuitive API and rich feature set, you can easily create complex routing patterns and keep your code organized and maintainable.

## Exercises

1.  Create a multi-page React application that has a home page and an about page. Use React Router to route between these pages.
    
2.  Add a new route to your application that displays a contact page. The contact page should have a form that allows users to submit a message.
    
3.  Create a navigation menu that allows users to navigate between the different pages of your application.
    
4.  Use nested routes to create a blog section on your website. The blog section should have a main page that lists all the blog posts, and a subpage for each individual blog post.
    
5.  Use URL parameters to create a product page on your website. The product page should display information about a specific product based on the URL parameter.
    
6.  Implement a 404 page that is displayed when a user navigates to a page that doesn't exist.
    
7.  Create a private route that requires authentication before allowing access to a certain page. Use a boolean variable to simulate authentication.
    

These exercises should help you get familiar with React Router and give you practice in creating multi-page applications with dynamic routing.