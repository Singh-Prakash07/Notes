### What is Node.js? 🤔
+ Simply put, Node.js is a way to run JavaScript on your computer (a server), not just in a web browser.
+ Think of JavaScript in a browser as being in a sandbox—it can only interact with the webpage. Node.js takes the powerful V8 JavaScript engine (the same one used in Google Chrome) and lets it run on your machine, giving it "superpowers" to access things like the file system, databases, and network connections.

#### Key Features:
+ JavaScript Runtime Environment: It's not a language or a framework; it's a platform for executing JavaScript code on the back-end.
+ Asynchronous and Non-blocking: This is its most famous feature. Instead of waiting for a task (like reading a file) to finish, Node.js can start that task, move on to other work, and come back when the first task is complete. This makes it incredibly efficient for applications that handle many simultaneous connections, like chat apps or APIs.
+ Analogy: A traditional "blocking" waiter takes your order, goes to the kitchen, and waits for your food before serving anyone else. A Node.js "non-blocking" waiter takes your order, gives it to the kitchen, and then immediately takes orders from other tables while the food is being prepared.
+ NPM (Node Package Manager): It comes with the world's largest ecosystem of open-source libraries, making it easy to add functionality to your projects.
### 1. Installation
+ Getting Node.js is straightforward.
+ Go to the official website: nodejs.org
+ Download the installer: You'll see two options:
+ LTS (Long-Term Support): This is the recommended version for most users, especially beginners. It's the most stable and reliable.
+ Current: This version has the latest features but might have more bugs.
+ Run the installer: Follow the on-screen instructions. It will install both node and npm.
+ Verify the installation: Open your terminal (Command Prompt, PowerShell, or Terminal on Mac/Linux) and type these commands:
+ Bash
```
# Check Node.js version
node -v
# Check NPM version
npm -v
```
+ If they return version numbers (e.g., v20.11.1), you're all set!

### 2. Your First "Hello, World!" Program
+ Let's run some Node.js code.
+ Create a file: Create a new file named app.js.
+ Write the code: Add the following line to app.js:
+ JavaScript
```
console.log("Hello, Node.js World!");
```
+ Run from the terminal: Navigate to the directory where you saved app.js and run the following command:
+ Bash: `node app.js`
+ You should see "Hello, Node.js World!" printed in your terminal. You've just executed your first Node.js program!

### 3. Core Concepts: Modules
+ In Node.js, you organize your code into reusable pieces called modules. Think of them like LEGO bricks for your application. There are three main types:

1. Core Modules: These are built directly into Node.js. You just need to ask for them. Key examples include:
  + http: For creating web servers.
  + fs (File System): For reading and writing files.
  + path: For working with file and directory paths.
  + Example (using fs):
  + JavaScript
  ```
    // Import the 'fs' module
    const fs = require('fs');
    // Write content to a file named 'welcome.txt'
    fs.writeFileSync('welcome.txt', 'Hello from Node.js!');
  ```
2. Local Modules: These are modules you create yourself. You export functionality from one file and import it into another.
  + Example: math.js (our module)
  + JavaScript
  ```
    const add = (a, b) => a + b;
    const subtract = (a, b) => a - b;
    // Export the functions to make them available elsewhere
    module.exports = { add, subtract };
    app.js (where we use our module)
    # another example
    // Import our local math module (note the './')
    const math = require('./math.js');
    console.log("Addition:", math.add(5, 3)); // Output: Addition: 8
    console.log("Subtraction:", math.subtract(5, 3)); // Output: Subtraction: 2
  ```
3. Third-Party Modules: These are modules created by other developers that you can download using NPM.

### 4. NPM: Node Package Manager 📦
+ NPM is your best friend in the Node.js world. It's a command-line tool that helps you manage the external libraries (packages) your project depends on.
+ package.json: This file is the heart of any Node.js project. It lists project details and, most importantly, all the third-party packages it needs.
+ To create one, run npm init -y in your project folder.
+ Installing a package: To add a package, you use npm install. Let's install a popular utility library called lodash.
+ Bash : `npm install lodash`
+ This command does two things:
+ Downloads the lodash code into a new folder called node_modules.
+ Adds lodash as a dependency in your package.json file.
+ Using the package:
+ JavaScript
```
// Import the third-party module
const _ = require('lodash');
const randomNumber = _.random(1, 100);
console.log(`Here is a random number: ${randomNumber}`);
```
### 5. Building a Simple Web Server
+ This is where Node.js truly shines. Let's create a basic server that responds to web requests using the built-in http module.
+ Create a file named server.js.
+ Add the following code:
+ JavaScript
```
// 1. Import the http module
const http = require('http');

// 2. Define the server's host and port
const hostname = '127.0.0.1'; // This means localhost
const port = 3000;

// 3. Create the server
// The createServer method takes a function that runs for every request
const server = http.createServer((req, res) => {
  // req = request (what the user is asking for)
  // res = response (what we send back)

  res.statusCode = 200; // 200 means "OK"
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello from my first Node.js Server!\n');
});

// 4. Start the server and make it listen for requests
server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
Run the server from your terminal: node server.js.

Open your web browser and go to http://localhost:3000. You'll see your message!
```

### 6. Introduction to Express.js
+ While you can build servers with the http module, it's very low-level. For real applications, almost everyone uses a framework. Express.js is the most popular and minimalist web framework for Node.js. It simplifies tasks like routing and handling requests.
+ Install Express: npm install express
+ Create an Express server (express-server.js):
+ JavaScript
```
const express = require('express');
const app = express(); // Create an Express application
const port = 3000;

// Define a route for the root URL ('/')
// When someone visits our homepage, this function will run
app.get('/', (req, res) => {
  res.send('Hello from my first Express Server!');
});

// Start the server
app.listen(port, () => {
  console.log(`Express server listening at http://localhost:${port}`);
});
```
+ Notice how much cleaner this is! Express handles the complex parts of the http module for you.

## Next
+ Express Deep Dive: about routing, middleware, and serving static files.
+ APIs: Build REST APIs that send and receive JSON data.
+ Databases: Connect your Node.js app to databases like MongoDB (with Mongoose) or PostgreSQL (with Sequelize).
+ Asynchronous JavaScript: Master concepts like Callbacks, Promises, and async/await to handle non-blocking operations gracefully.
