# Session 7 - Part 2: useReducer Hook

The `useReducer` hook in React provides a way to manage state in functional components using a reducer function. It is similar to the state management pattern used in Redux.

## How to use `useReducer`

The `useReducer` hook can be used to manage state in a functional component by creating a reducer function that handles updates to the state. Here's an example:

```jsx
import { useReducer } from "react";
const initialState = { count: 0 };
function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}
function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <div>
      {" "}
      <p>Count: {state.count}</p>{" "}
      <button onClick={() => dispatch({ type: "increment" })}>+</button>{" "}
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>{" "}
    </div>
  );
}
```

In this example, the `useReducer` hook is used to manage state for a counter. The `reducer` function handles updates to the state based on the `type` property of the action passed to the `dispatch` function. The `Counter` component uses the `state` returned by `useReducer` and the `dispatch` function to update the state when the buttons are clicked.

## Benefits of `useReducer`

Using `useReducer` to manage state in React has several benefits:

*   **Predictable state changes:** Because all updates to the state are handled by the reducer function, it is easier to predict and debug state changes in a complex application.
    
*   **Separation of concerns:** By separating the state management logic into a reducer function, it is easier to manage state across multiple components without duplicating code.
    
*   **Better performance:** Since `useReducer` does not cause unnecessary re-renders, it can lead to better performance in large and complex applications.


## Example

### Managing a Shopping Cart

```jsx
import { useReducer } from "react";
const initialState = { items: [], total: 0 };
function reducer(state, action) {
  switch (action.type) {
    case "add":
      const newItem = action.payload;
      const newItems = [...state.items, newItem];
      const newTotal = state.total + newItem.price;
      return { items: newItems, total: newTotal };
    case "remove":
      const removedItem = action.payload;
      const removedItems = state.items.filter(
        (item) => item.id !== removedItem.id
      );
      const removedTotal = state.total - removedItem.price;
      return { items: removedItems, total: removedTotal };
    default:
      throw new Error();
  }
}
function ShoppingCart() {
  const [state, dispatch] = useReducer(reducer, initialState);
  const handleAddItem = (item) => {
    dispatch({ type: "add", payload: item });
  };
  const handleRemoveItem = (item) => {
    dispatch({ type: "remove", payload: item });
  };
  return (
    <div>
      {" "}
      <h2>Shopping Cart</h2> <p>Total: ${state.total.toFixed(2)}</p>{" "}
      <ul>
        {" "}
        {state.items.map((item) => (
          <li key={item.id}>
            {" "}
            {item.name} - ${item.price.toFixed(2)}{" "}
            <button onClick={() => handleRemoveItem(item)}>Remove</button>{" "}
          </li>
        ))}{" "}
      </ul>{" "}
      <button
        onClick={() => handleAddItem({ id: 1, name: "Item 1", price: 10 })}
      >
        Add Item
      </button>{" "}
    </div>
  );
}
```

In this example, the `useReducer` hook is used to manage state for a shopping cart. The `reducer` function handles updates to the state based on the `type` property of the action passed to the `dispatch` function. The `ShoppingCart` component uses the `state` returned by `useReducer` and the `dispatch` function to update the state when the `Add Item` and `Remove` buttons are clicked.

## Exercises 

1.  Create a component that manages a boolean state value using `useReducer`. The component should display a button that toggles the state value when clicked.
    
2.  Create a component that manages a numeric state value using `useReducer`. The component should display the current value and two buttons that increment and decrement the value.
    
3.  Create a component that manages a list of strings using `useReducer`. The component should allow the user to add and remove items from the list using a form input and a button.
    
4.  Create a component that manages a form's state using `useReducer`. The component should allow the user to enter a name and email address and display the values when submitted.
    
5.  Create a component that manages a simple shopping cart using `useReducer`. The component should allow the user to add and remove items from the cart and display the total cost of the items.
    

These exercises will help you get comfortable with using `useReducer` in different scenarios and give you a better understanding of how it works.