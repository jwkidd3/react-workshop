# Session 10 - Part 4: Route Parameters

Route parameters are dynamic values that can be added to the URL of a specific route. These dynamic values can be used to fetch data from a backend API, filter content on a page, or create dynamic routes for user-specific pages. In React Router, route parameters are defined with a colon (`:`) followed by the parameter name in the path of a Route component.

For example, let's say you have a list of users and you want to display the details of a specific user when the user clicks on their name. You can define a dynamic route parameter for the user ID like this:

```jsx
import { Switch, Route } from "react-router-dom";
function App() {
  return (
    <Switch>
      {" "}
      <Route path="/users/:id">
        {" "}
        <UserDetails />{" "}
      </Route>{" "}
    </Switch>
  );
}
```

In this example, the `:id` is a dynamic route parameter that can match any value after the `/users/` path segment. For example, if the user clicks on a link to `/users/123`, the `:id` parameter will be set to `"123"`.

You can access the value of the `:id` parameter in your component by using the `useParams` hook from React Router:

```jsx
import { useParams } from "react-router-dom";
function UserDetails() {
  const { id } = useParams(); // use the id value to fetch user data from an API or display user details
  return (
    <div>
      {" "}
      <h2>User Details for ID: {id}</h2>
      {/* display user details */}
    </div>
  );
}
```

In this example, the `useParams` hook extracts the value of the `:id` parameter from the URL and assigns it to the `id` constant. You can then use this value to fetch the user details from a backend API or display the details on the page.

Route parameters can also be optional by using the `?` character after the parameter name. For example:

```jsx
import { Switch, Route } from "react-router-dom";
function App() {
  return (
    <Switch>
      {" "}
      <Route path="/users/:id?">
        {" "}
        <UserDetails />{" "}
      </Route>{" "}
    </Switch>
  );
}
```

In this example, the `:id` parameter is optional and can be omitted from the URL. If the user visits `/users`, the `id` value will be `undefined`.

Route parameters can also have a regular expression to match only specific values. For example:

```jsx
import { Switch, Route } from "react-router-dom";
function App() {
  return (
    <Switch>
      {" "}
      <Route path="/users/:id(\d+)">
        {" "}
        <UserDetails />{" "}
      </Route>{" "}
    </Switch>
  );
}
```

In this example, the `:id` parameter will only match numeric values, such as `/users/123`. If the user visits a URL like `/users/abc`, the route won't match and the user won't see the `UserDetails` component.

That's a basic overview of how route parameters work in React Router. They can be incredibly powerful for creating dynamic, data-driven applications.

## Examples

### Basic Route Parameters

Let's say we have a simple application that displays a list of users and we want to be able to click on a user to see their profile. We can use route parameters to achieve this.

First, we'll set up our `App.js` file with the `BrowserRouter` component and two routes, one for the home page and one for the user profile page:


```jsx
import { BrowserRouter, Route } from "react-router-dom";
import HomePage from "./HomePage";
import UserProfilePage from "./UserProfilePage";
function App() {
  return (
    <BrowserRouter>
      {" "}
      <Route exact path="/" component={HomePage} />{" "}
      <Route exact path="/users/:userId" component={UserProfilePage} />{" "}
    </BrowserRouter>
  );
}
export default App;
```

In this example, we've defined a route parameter called `:userId` in the path for the user profile page. When a user clicks on a user's name in the home page, the `UserProfilePage` component will be rendered with the appropriate `userId` passed in as a parameter.

We can access the value of the `userId` parameter inside the `UserProfilePage` component using the `useParams` hook provided by `react-router-dom`. Here's an example implementation of the `UserProfilePage` component:

```jsx
import { useParams } from "react-router-dom";
function UserProfilePage() {
  const { userId } = useParams();
  return (
    <div>
      {" "}
      <h1>User Profile Page</h1>{" "}
      <p>Showing profile for user with ID {userId}</p>{" "}
    </div>
  );
}
export default UserProfilePage;
```

In this example, we're using the `useParams` hook to get the value of the `userId` parameter from the URL. We can then use this value to display the appropriate user profile information.

### Optional Route Parameters

Sometimes we may want to have optional route parameters, where the parameter may or may not be present in the URL. We can achieve this using the `?` symbol in our route path.

Let's say we have an application that displays a list of products, and we want to be able to filter the products based on certain criteria. We can use an optional route parameter to achieve this.

Here's an example implementation of the `ProductListPage` component with an optional `category` parameter:

```jsx
import { Link, Route, Switch, useParams } from "react-router-dom";
import ProductList from "./ProductList";
function ProductListPage() {
  return (
    <div>
      {" "}
      <h1>Product List Page</h1>{" "}
      <nav>
        {" "}
        <ul>
          {" "}
          <li>
            <Link to="/products">All Products</Link>
          </li>{" "}
          <li>
            <Link to="/products/category/electronics">Electronics</Link>
          </li>{" "}
          <li>
            <Link to="/products/category/clothing">Clothing</Link>
          </li>{" "}
        </ul>{" "}
      </nav>{" "}
      <Switch>
        {" "}
        <Route exact path="/products" component={ProductList} />{" "}
        <Route
          exact
          path="/products/category/:category?"
          component={ProductList}
        />{" "}
      </Switch>{" "}
    </div>
  );
}
export default ProductListPage;
```

In this example, we've defined an optional `category` parameter in the path for the product list page. When the user clicks on one of the category links, the `ProductList` component will be rendered with the appropriate filter applied.

We can access the value of the `category` parameter inside the `ProductList` component using the `useParams` hook just like we did in the previous example.

### Query Parameters

Query parameters allow us to pass additional data in the URL after a question mark `?`. These parameters are typically used for filtering or searching data, but can be used for any additional data needed for a route.

To access query parameters in React Router, we can use the `useLocation` hook from `react-router-dom`. The `useLocation` hook returns an object containing the current URL's query string as a key/value object.

Here's an example:

```jsx
import { useLocation } from "react-router-dom";
function SearchResults() {
  const location = useLocation();
  const searchParams = new URLSearchParams(location.search);
  const query = searchParams.get("q");
  return (
    <div>
      {" "}
      <h2>Search Results for "{query}"</h2> {/* Display search results */}{" "}
    </div>
  );
}
function App() {
  return (
    <BrowserRouter>
      {" "}
      <Switch>
        {" "}
        <Route exact path="/" component={Home} />{" "}
        <Route path="/search" component={SearchResults} />{" "}
      </Switch>{" "}
    </BrowserRouter>
  );
}
```

In this example, we have a `SearchResults` component that displays search results based on a query parameter. We use the `useLocation` hook to get the current location object, which includes the query string. We then create a new `URLSearchParams` object to parse the query string and get the value of the `q` parameter.

Note that we could also use the `location.search` string directly instead of creating a new `URLSearchParams` object, but using the `URLSearchParams` API gives us some useful methods for working with query parameters.

In the `App` component, we define a route for `/search` that renders the `SearchResults` component.

Query parameters can be added to links using the `Link` component by passing an object with a `search` property to the `to` prop. For example:

```jsx
  <Link to={{ pathname: "/search", search: "?q=query" }}>Search</Link>
```

This would create a link to `/search?q=query`, which would trigger the `SearchResults` component to render with the query parameter set to "query".

Overall, query parameters provide a powerful way to pass additional data between components and pages in your React app.

## Exercises

1. Create a new ReactJS project and add a new component called "ProductDetails". This component should display the details of a product using route parameters.

2. Create a new component called "UserDetails". This component should display the details of a user using route parameters.

3. Create a new component called "ArticleDetails". This component should display the details of an article using route parameters.

4. Add a new route to your project that takes a parameter "id". This route should display the details of a post using the "id" parameter.

5. Modify the previous exercise to display the details of a post using a dynamic URL, for example "/post/:id".

6. Create a new component called "CategoryDetails". This component should display the details of a category using route parameters.

7. Modify the previous exercise to display the details of a category using a dynamic URL, for example "/category/:id".

8. Add a new route to your project that takes two parameters "categoryId" and "postId". This route should display the details of a post within a specific category.

9. Modify the previous exercise to display the details of a post within a specific category using a dynamic URL, for example "/category/:categoryId/post/:postId".

10. Create a new component called "TagDetails". This component should display the details of a tag using route parameters.

11. Modify the previous exercise to display the details of a tag using a dynamic URL, for example "/tag/:id".

12. Create a new component called "SearchResults". This component should display the search results using route parameters.

13. Modify the previous exercise to display the search results using a dynamic URL, for example "/search/:query".

14. Add a new route to your project that takes a parameter "username". This route should display the profile of a user using the "username" parameter.

15. Modify the previous exercise to display the profile of a user using a dynamic URL, for example "/profile/:username".
