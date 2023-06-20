# Session 3 - Part 2: Modules

In NodeJS, a module is a self-contained piece of code that exports values and can be imported into other parts of a NodeJS application. Modules are used to break up large applications into smaller, more manageable pieces, and to provide reusable components that can be shared between multiple applications.

NodeJS provides a number of built-in modules, such as the `fs` module for working with the file system, the `http` module for making HTTP requests, and more. In addition to the built-in modules, NodeJS also supports the use of third-party modules through the use of NPM (Node Package Manager).

NPM is the default package manager for NodeJS and is used to manage the packages or dependencies required for a NodeJS project. To use a third-party module in a NodeJS project, you need to install it using NPM.

One popular third-party module for making HTTP requests in NodeJS is `axios`. To install `axios` using NPM, you can use the following command:

```bash
npm install axios
```

Once `axios` is installed, you can import it into your NodeJS application using the `require` function. For example:

```js
const axios = require('axios');
axios.get('https://jsonplaceholder.typicode.com/posts').then(response => {
	console.log(response.data);
}).catch(error => {
	console.error(error);
});
```

This example demonstrates how you can use the `axios` module to make a GET request to a REST API and log the response data to the console.

Overall, modules play a critical role in the development of NodeJS applications, allowing developers to break up their applications into smaller, more manageable pieces, and to easily reuse code across multiple projects. The use of NPM makes it easy to install and manage third-party modules, providing developers with access to a vast library of pre-existing code that they can use to add functionality to their projects.

## Examples

The following examples demonstrate the use of modules in NodeJS and installing modules using NPM.

```js
// Example of using a built-in NodeJS module 
const fs = require('fs');
fs.readFile('./file.txt', 'utf-8', (err, data) => {
	if (err) {
		console.error(err);
	} else {
		console.log(data);
	}
});

// Example of using a third-party module installed using NPM
const axios = require('axios');
axios.get('https://jsonplaceholder.typicode.com/posts').then(response => {
	console.log(response.data);
}).catch(error => {
	console.error(error);
});

// Example of using a built-in NodeJS module  const http = require('http'); 
const requestListener = function(req, res) {
	res.writeHead(200);
	res.end('Hello, World!');
}
const server = http.createServer(requestListener);
server.listen(3000, () => {
	console.log('Server is running on port 3000');
});

// Example of using a third-party module installed using NPM 
const moment = require('moment');
console.log(moment().format('MMMM Do YYYY, h:mm:ss a'));
```

In the first example, we are using the built-in `fs` module to read the contents of a file. In the second example, we are using the `axios` module to make a GET request to a REST API and log the response data to the console. In the third example, we are using the built-in `http` module to create a simple HTTP server and listen on port 3000. In the fourth example, we are using the `moment` module, which is installed using NPM, to format the current date and time.

These examples demonstrate the versatility of using modules in NodeJS and the ease of installing third-party modules using NPM. Whether you are working with the file system, making HTTP requests, creating a server, or formatting dates, modules provide a way to add functionality to your applications in a modular, reusable way.