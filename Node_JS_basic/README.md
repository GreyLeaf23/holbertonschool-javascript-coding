# NodeJS Basics Learning!




# General Questions:




## What is NodeJS?
Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that runs on the V8 engine and executes JavaScript code
outside a web browser. Node.js lets developers use JavaScript to write command line tools and for server-side scripting—running scripts
server-side to produce dynamic web page content before the page is sent to the user's web browser. Consequently, Node.js represents a
"JavaScript everywhere" paradigm, unifying web application development around a single programming language, rather than different languages
for server-side and client-side scripts.




## How to run javascript using NodeJS?
To run JavaScript using Node.js, follow these steps:

1. Install Node.js on your machine if you haven't already. You can download it from the official Node.js website.

2. Create a JavaScript file. For example, you can create a file named `app.js`.

3. Write your JavaScript code in the `app.js` file. For example:
```javascript
console.log("Hello, World!");
```

4. Open your terminal or command prompt.

5. Navigate to the directory where your `app.js` file is located using the `cd` command.

6. Run the JavaScript file using Node.js by typing the following command and then pressing Enter:
```bash
node app.js
```

7. The output of your JavaScript code will be displayed in the terminal. In this case, you should see `Hello, World!`.




## How to use NodeJS modules?
Node.js has a built-in module system. You can include modules in your program using the `require` function. Here's a basic example:

1. Create a new JavaScript file named `module.js`:

```javascript
// module.js
exports.myDateTime = function () {
  return Date();
};
```

In this file, we define a function named `myDateTime` and use `exports` to make it accessible from other files.

2. Create another JavaScript file named `app.js`:

```javascript
// app.js
var dt = require('./module.js');
console.log(dt.myDateTime());
```

In this file, we use `require` to include the `module.js` file. We can then use the `myDateTime` function that we exported from `module.js`.

3. Run `app.js` with Node.js:

```bash
node app.js
```

This will print the current date and time to the console, as returned by the `myDateTime` function from `module.js`.

Note: The `./` in `require('./module.js')` is used to locate the `module.js` file. It means that the file is in the same directory as the
current file (`app.js`). If your file was in a `modules` directory, for example, you would use `require('./modules/module.js')`.




## How to use specific Node JS module to read files?
To read files in Node.js, you can use the built-in `fs` (File System) module. Here's an example of how to use it:

1. Include the `fs` module in your program:

```javascript
var fs = require('fs');
```

2. Use the `readFile` function to read a file. This function takes the file path and a callback function as arguments. The callback function
will be called when the file has been read:

```javascript
fs.readFile('test.txt', 'utf8', function(err, data) {
  if (err) throw err;
  console.log(data);
});
```

In this example, `test.txt` is the file to be read, and `'utf8'` is the file's character encoding. The callback function takes two
arguments: `err` (an error object) and `data` (the file's contents).

3. Run your program with Node.js:

```bash
node app.js
```

This will print the contents of `test.txt` to the console. If an error occurs (for example, if the file does not exist), an exception will
be thrown.




## How to use *process* to access command line arguments and the environment?
In Node.js, the `process` object provides information about, and control over, the current Node.js process. It can be used to access command
line arguments and the environment.

1. **Accessing Command Line Arguments**

Command line arguments can be accessed via `process.argv`, which is an array containing the command line arguments. The first element will
be 'node', the second element will be the name of the JavaScript file. The next elements will be any additional command line arguments.

Here's an example:

```javascript
// Print process.argv
process.argv.forEach((val, index) => {
  console.log(`${index}: ${val}`);
});
```

If you run this script with `node app.js one two=three four`, the output will be:

```bash
0: node
1: /path/to/your/app.js
2: one
3: two=three
4: four
```

2. **Accessing the Environment**

The `process.env` property returns an object containing the user environment. For example, to access the `PATH` environment variable, you
can use `process.env.PATH`.

Here's an example:

```javascript
// Print the PATH environment variable
console.log(`Your PATH is: ${process.env.PATH}`);
```

This will print the `PATH` environment variable to the console.




## How to create a small HTTP server using Node JS?
You can create a small HTTP server using the built-in `http` module in Node.js. Here's a basic example:

1. Include the `http` module in your program:

```javascript
var http = require('http');
```

2. Use the `createServer` method to create an HTTP server:

```javascript
var server = http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
});
```

In this example, the server will respond with "Hello World" for every request.

3. Start the server:

```javascript
server.listen(3000, function() {
  console.log('Server is running at http://localhost:3000/');
});
```

In this example, the server is running at port 3000.

4. Run your program with Node.js:

```bash
node app.js
```

You can now visit `http://localhost:3000` in your web browser to see the message "Hello World".




## How to create a small HTTP server using Express JS?
Express.js is a popular web application framework for Node.js. Here's how you can create a small HTTP server using Express.js:

1. First, you need to install Express.js. You can do this using npm (Node Package Manager), which is included with Node.js. In your
terminal, run:

```bash
npm install express
```

2. Create a new JavaScript file (for example, `app.js`), and include the Express module:

```javascript
var express = require('express');
var app = express();
```

3. Define a route for the server:

```javascript
app.get('/', function (req, res) {
  res.send('Hello World!');
});
```

In this example, the server will respond with "Hello World!" when you access the root URL (`/`).

4. Start the server:

```javascript
app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
});
```

In this example, the server is running at port 3000.

5. Run your program with Node.js:

```bash
node app.js
```

You can now visit `http://localhost:3000` in your web browser to see the message "Hello World!".




## How to create advanced routes with Express JS?
Express.js allows you to create advanced routes using route parameters, query parameters, and HTTP verbs. Here's an example:

1. Include the Express module:

```javascript
var express = require('express');
var app = express();
```

2. Define a route with a route parameter:

```javascript
app.get('/users/:userId', function (req, res) {
  res.send('User ID is: ' + req.params.userId);
});
```

In this example, `:userId` is a route parameter. You can access its value with `req.params.userId`.

3. Define a route with a query parameter:

```javascript
app.get('/search', function (req, res) {
  res.send('Search term is: ' + req.query.q);
});
```

In this example, `q` is a query parameter. You can access its value with `req.query.q`.

4. Define routes for different HTTP verbs:

```javascript
app.get('/books', function (req, res) {
  res.send('Get a random book');
});

app.post('/books', function (req, res) {
  res.send('Add a book');
});

app.put('/books/:id', function (req, res) {
  res.send('Update the book with id ' + req.params.id);
});
```

In this example, we define routes for the `GET`, `POST`, and `PUT` HTTP verbs.

5. Start the server:

```javascript
app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
});
```

6. Run your program with Node.js:

```bash
node app.js
```

You can now visit `http://localhost:3000/users/123` to see the message "User ID is: 123", `http://localhost:3000/search?q=express` to see
the message "Search term is: express", and so on.




## How to use ES6 with Node JS with Babel-node?
To use ES6 features with Node.js, you can use Babel, a JavaScript compiler that can convert ES6 code into ES5 code, which is compatible with
Node.js. Here's how you can set it up:

1. First, initialize a new npm project if you haven't already. In your terminal, run:

```bash
npm init -y
```

2. Install Babel and the necessary presets. In your terminal, run:

```bash
npm install --save-dev @babel/core @babel/node @babel/preset-env
```

3. Create a `.babelrc` file in your project root and add the following configuration:

```json
{
  "presets": ["@babel/preset-env"]
}
```

This tells Babel to use the preset-env, which allows you to use ES6 features.

4. Now, you can use `babel-node` instead of `node` to run your scripts. For example:

```bash
npx babel-node your-script.js
```

5. If you want to use `babel-node` for your npm start script, you can add the following to your `package.json`:

```json
"scripts": {
  "start": "babel-node your-script.js"
}
```

Now, you can use `npm start` to run your script with Babel.

Remember, `babel-node` is not meant for production use. It's recommended to compile your files ahead of time for production use. You can do
this by running `npx babel your-script.js --out-file your-compiled-script.js` and then use Node.js to run the compiled script.




## How to use Nodemon to develop faster?
Nodemon is a utility that will monitor for any changes in your source and automatically restart your server. This can significantly speed up
your development process. Here's how to use it:

1. First, install Nodemon as a development dependency in your project. In your terminal, run:

```bash
npm install --save-dev nodemon
```

2. Then, in your `package.json` file, change the `start` script to use `nodemon` instead of `node`:

```json
"scripts": {
  "start": "nodemon your-script.js"
}
```

3. Now, you can start your application with `npm start`. Nodemon will watch for changes to your files and restart your application whenever
it detects a change.

4. If you're using Babel in your project, you can use Nodemon with `babel-node` like this:

```json
"scripts": {
  "start": "nodemon --exec babel-node your-script.js"
}
```

This will start your application with `babel-node` and restart it whenever Nodemon detects a change.
