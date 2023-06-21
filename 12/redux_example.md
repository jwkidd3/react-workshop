Set up a new React project or use an existing one. Make sure you have Node.js and npm (Node Package Manager) installed.

Install the necessary dependencies by running the following command in your project directory:
npm install react react-dom react-redux redux

Create a new file called index.js and add the following code:
import React from 'react';
import ReactDOM from 'react-dom';
import { createStore } from 'redux';
import { Provider, connect } from 'react-redux';

// Step 3: Define Redux reducers
const initialState = {
  count: 0
};

const reducer = (state = initialState, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { ...state, count: state.count + 1 };
    case 'DECREMENT':
      return { ...state, count: state.count - 1 };
    default:
      return state;
  }
};

const store = createStore(reducer);

// Step 5: Connect React components to Redux store
class Counter extends React.Component {
  render() {
    const { count, increment, decrement } = this.props;

    return (
      <div>
        <h2>Count: {count}</h2>
        <button onClick={increment}>Increment</button>
        <button onClick={decrement}>Decrement</button>
      </div>
    );
  }
}

const mapStateToProps = (state) => ({
  count: state.count
});

const mapDispatchToProps = (dispatch) => ({
  increment: () => dispatch({ type: 'INCREMENT' }),
  decrement: () => dispatch({ type: 'DECREMENT' })
});

const ConnectedCounter = connect(mapStateToProps, mapDispatchToProps)(Counter);

// Step 6: Wrap the root component with the Provider and provide the Redux store
ReactDOM.render(
  <Provider store={store}>
    <ConnectedCounter />
  </Provider>,
  document.getElementById('root')
);

Create an HTML file, such as index.html, in the same directory and add the following code:
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>React Redux Counter</title>
</head>
<body>
  <div id="root"></div>
  <script src="index.js"></script>
</body>
</html>

Open the HTML file in a web browser, and you should see a counter with buttons to increment and decrement the count value. The state of the counter is managed by Redux.

The example sets up a Redux store using createStore from the 'redux' package. It defines a reducer that handles incrementing and decrementing the count state. The connect function is used to connect the Counter component to the Redux store, allowing it to access the state and dispatch actions. The root component, ConnectedCounter, is wrapped with the Provider component from React Redux to provide the Redux store to all connected components. The rendered result is inserted into the div with the id "root" in the HTML file.

By clicking the "Increment" and "Decrement" buttons, the count value will be updated and displayed in the UI.

