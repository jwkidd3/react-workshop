# Session 3 - Part 1: Introduction to NodeJS and NPM

Node.js is a JavaScript runtime environment that allows developers to run JavaScript on the server-side. It provides a fast and efficient platform for building server-side applications using JavaScript.

NPM (Node Package Manager) is the default package manager for Node.js and is used to manage the packages or dependencies required for a Node.js project. It allows developers to easily install, update, and manage packages that are used in their projects.

Node.js and NPM are widely used by developers to build web applications, command-line tools, and other types of applications. Node.js provides a number of built-in modules, such as the HTTP module, that makes it easy to build server-side applications. NPM provides a vast library of packages that developers can use to add functionality to their projects, such as authentication, data storage, and more.

Setting up NodeJS and NPM is a straightforward process. You can download the latest version of NodeJS from the official website and follow the installation instructions. Once you have installed NodeJS, you can use the npm command-line tool to install and manage packages for your project.

To check if NodeJS and NPM are installed, you can run the following bash commands:

```bash
node -v
npm -v
```

These commands will display the version number of NodeJS and NPM, respectively. If you see a version number, then NodeJS and NPM are installed and ready to use.

It's important to note that executing JavaScript code in NodeJS is different from executing it in a browser. In a browser, JavaScript is executed in the context of a web page, and has access to the Document Object Model (DOM) and the window object. In NodeJS, JavaScript is executed in a standalone environment, and does not have access to the DOM or the window object. Instead, NodeJS provides a number of built-in modules for working with the file system, making HTTP requests, and more.

Overall, Node.js and NPM are essential tools for any developer looking to build server-side applications with JavaScript. With their fast performance, extensive libraries, and ease of use, they are a popular choice for building high-quality and scalable applications.

## Examples

The following example demonstrates the difference between executing JavaScript code in NodeJS and in a browser, including the differences in access to the `window` object.

```js
// Example of JavaScript code executed in NodeJS
const os = require('os');
console.log(os.platform());


// Example of JavaScript code executed in a browser 
console.log(window.navigator.platform); 
window.alert('Hello, World!');
```

In the NodeJS example, we are using the built-in `os` module to retrieve information about the operating system. In the browser example, we are using the `window.navigator.platform` property to retrieve information about the platform, and using the `window.alert` method to display a message to the user.

It's important to note that the `os` module is not available in the browser, as the browser does not have direct access to the underlying operating system. Similarly, the `window` object is not available in NodeJS, as NodeJS is a server-side environment and does not have access to the user's browser.

This example demonstrates the different capabilities and limitations of executing JavaScript code in NodeJS and in a browser, and highlights the importance of understanding the context in which your code is being executed.