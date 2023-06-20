# Session 4 - Part 5: Import/Export in JS

In NodeJS, the `require` function and the `module.exports` object are used to include code from one module into another. For example:

```js
// math.js
function add(a, b) {
	return a + b;
}

function subtract(a, b) {
	return a - b;
}
module.exports = {
	add,
	subtract
};
```

```js
// index.js
const {
	add,
	subtract
} = require('./math');
console.log(add(1, 2));
console.log(subtract(1, 2));
```

In this example, the `add` and `subtract` functions are exported from the `math.js` module using `module.exports`, and then required and used in the `index.js` module. This is an example of named exports.

You can also use `module.exports` to export a single default value or function:

```js
// math.js 
function add(a, b) {
	return a + b;
}
module.exports = add;
```

```js
// index.js
const add = require('./math');
console.log(add(1, 2));
```

In this example, the `add` function is exported as the default value from the `math.js` module using `module.exports`, and then required and used in the `index.js` module.

In JavaScript, the `import` and `export` statements are used to include code from one module into another. For example, in a React-based application:

```js
// Math.js  
export function add(a, b) {
	return a + b;
}
export function subtract(a, b) {
	return a - b;
}
```

```js
// App.js
import { add, subtract } from "./Math";
function App() {
  return (
    <div>
      {" "}
      {add(1, 2)} {subtract(1, 2)}{" "}
    </div>
  );
}
```

In this example, the `add` and `subtract` functions are exported from the `Math.js` module using the `export` statement, and then imported and used in the `App.js` component. This is an example of named exports.

You can also use the `export default` syntax to export a single default value or function:

```js
// Math.js 
export default function add(a, b) {
	return a + b;
```

```js
// App.js
import add from "./Math";
function App() {
  return <div>{add(1, 2)}</div>;
}
```

In this example, the `add` function is exported as the default value from the `Math.js` module using the `export default` syntax, and then imported and used in the `App.js` component.

The key difference between `require` and `module.exports` in NodeJS and `import` and `export` in JavaScript is the syntax. The concepts are similar, but the syntax is different. In NodeJS, you use `require` to include code from another module, and `module.exports` to export values or functions. In JavaScript, you use `import` to include code from another module, and `export` to export values or functions. Both examples demonstrate the use of named exports, which allows you to export multiple values or functions from a single module.