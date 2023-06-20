# Session 10 - Part 1: Introduction to React-Router

In a typical web application, routing is handled on the server-side, where requests are sent to different endpoints based on the URL. However, in a single-page application, we need to handle routing on the client-side to avoid page reloads and provide a smooth user experience.

Without React-Router, we can handle routing in a single-page application by creating different components and rendering them based on the current URL. For example, suppose we have a simple application with two views: a home view and a contact view. We can create two components, `Home` and `Contact`, and render them conditionally based on the current URL:

```jsx
function App() {
  const [route, setRoute] = useState(window.location.pathname);
  useEffect(() => {
    window.onpopstate = () => {
      setRoute(window.location.pathname);
    };
  }, []);
  return (
    <div>
      {" "}
      {route === "/" && <Home />} {route === "/contact" && <Contact />}{" "}
    </div>
  );
}
```

In this example, we use the `useState` and `useEffect` hooks to update the route based on the current URL. We render the appropriate component based on the current route.

However, as the application grows in complexity, this approach can become unwieldy and difficult to maintain. This is where React-Router comes in. React-Router provides a simple, declarative way to handle routing in a single-page application, making it easier to create and manage complex routing scenarios.

With React-Router, we can define our routes using the `Route` component, and use the `Link` component to create links that navigate between different routes. React-Router also provides several other components, including `Switch` and `Redirect`, that can be used to implement more complex routing scenarios.

For example, we can define our routes using the `Route` component in the following way:

```jsx
import { Route } from "react-router-dom";
function App() {
  return (
    <div>
      {" "}
      <Route exact path="/" component={Home} />{" "}
      <Route path="/contact" component={Contact} />{" "}
    </div>
  );
}
```

In this example, we define two routes using the `Route` component. The `exact` prop is used to specify that the first route should only match when the path is exactly `/`. The `path` prop specifies the path to match, and the `component` prop specifies the component to render when the path is matched.

With React-Router, we can also use the `Link` component to create links that navigate between different routes:

```jsx
import { Link } from "react-router-dom";
function Navigation() {
  return (
    <nav>
      {" "}
      <ul>
        {" "}
        <li>
          <Link to="/">Home</Link>
        </li>{" "}
        <li>
          <Link to="/contact">Contact</Link>
        </li>{" "}
      </ul>{" "}
    </nav>
  );
}
```

In this example, we use the `Link` component to create links that navigate between the home and contact routes. The `to` prop specifies the path to navigate to when the link is clicked.

Overall, React-Router simplifies the process of handling routing in a single-page application and provides a more intuitive, scalable solution. In the next section, we will explore some examples of how to use React-Router in practice.

## Exercises

1.  Create a simple navigation menu using regular `<a>` tags without React-Router. Clicking on each link should take the user to a different page.
2.  Implement a search feature that filters a list of items based on user input. The search should be accessible from any page in the app.
3.  Create a "favorites" feature that allows users to add items to a list of their favorite content. Implement this feature across multiple pages without using React-Router.
4.  Implement a dynamic page that shows different content based on a URL parameter. For example, a page that displays a specific product based on its ID in the URL.
5.  Create a tabbed interface that shows different content in each tab. Clicking on a tab should change the content displayed on the page. This should be implemented without using React-Router.