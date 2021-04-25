# What Is Node and When Should I Use It? 


So you’ve heard of Node.js, but aren’t quite sure what it is or where it fits into your development workflow. Or maybe you’ve heard people singing Node’s praises and now you’re wondering if it’s something you need to learn. Perhaps you’re familiar with another back-end technology and want to find out what’s different about Node.

If that sounds like you, then keep reading. In this article, I’ll take a beginner-friendly, high-level look at Node.js and its main paradigms. I’ll examine Node’s main use cases, as well as the current state of the Node landscape, and offer you a wide range of jumping off points (for further reading) along the way.

Please note that, throughout the article, I’ll use “Node” and “Node.js” interchangeably.

What Is Node.js?
There are plenty of definitions to be found online. Let’s take a look at a couple of the more popular ones. This is what the project’s home page has to say:

Node.js® is a JavaScript runtime built on Chrome’s V8 JavaScript engine.

And this is what Stack Overflow has to offer:

Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.

Hmmm, “event-based”, “non-blocking”, “asynchronous I/O” — that’s quite a lot to digest in one go. So let’s approach this from a different angle and begin by focusing on the other detail that both descriptions mention — the V8 JavaScript engine.

Node Is Built on Google Chrome’s V8 JavaScript Engine
The V8 engine is the open-source JavaScript engine that runs in Google Chrome and other Chromium-based web browsers, including Brave, Opera, and Vivaldi. It was designed with performance in mind and is responsible for compiling JavaScript directly to native machine code that your computer can execute.

However, when we say that Node is built on the V8 engine, we don’t mean that Node programs are executed in a browser. They aren’t. Rather, the creator of Node (Ryan Dahl) took the V8 engine and enhanced it with various features, such as a file system API, an HTTP library, and a number of operating system–related utility methods.

This means that Node.js is a program we can use to execute JavaScript on our computers. In other words, it’s a JavaScript runtime.

How Do I Install Node.js?
In this next section, we’ll install Node and write a couple of simple programs. We’ll also look at npm, a package manager that comes bundled with Node.

Node Binaries vs Version Manager
Many websites will recommend that you head to the official Node download page and grab the Node binaries for your system. While that works, I would suggest that you use a version manager instead. This is a program that allows you to install multiple versions of Node and switch between them at will. There are various advantages to using a version manager. For example, it negates potential permission issues when using Node with npm and lets you set a Node version on a per-project basis.


If you fancy going the version manager route, please consult our quick tip: Install Multiple Versions of Node.js using nvm. Otherwise, grab the correct binaries for your system from the link above and install those.

“Hello, World!” the Node.js Way
You can check that Node is installed on your system by opening a terminal and typing node -v. If all has gone well, you should see something like v12.14.1 displayed. This is the current LTS version at the time of writing.

Next, create a new file hello.js and copy in the following code:

console.log("Hello, World!");
This uses Node’s built-in console module to display a message in a terminal window. To run the example, enter the following command:

node hello.js
If Node.js is configured properly, “Hello, World!” will be displayed.

Node.js Has Excellent Support for Modern JavaScript
As can be seen on this compatibility table, Node has excellent support for ECMAScript 2015 (ES6) and beyond. As you’re only targeting one runtime (a specific version of the V8 engine), this means that you can write your JavaScript using the latest and most modern syntax. It also means that you don’t generally have to worry about compatibility issues — as you would if you were writing JavaScript that would run in different browsers.





To illustrate the point, here’s a second program that makes use of several modern JavaScript features, such as tagged template literals, object destructuring and Array.prototype.flatMap():

function upcase(strings, ...values) {
  return values.map(name => name[0].toUpperCase() + name.slice(1))
    .join(' ') + strings[2];
}

const person = {
  first: 'brendan',
  last: 'eich',
  age: 56,
  position: 'CEO of Brave Software',
};

const { first, last } = person;
const emoticon = [ ['┌', '('], ['˘', '⌣'], ['˘', ')', 'ʃ'] ];

console.log(
  upcase`${first} ${last} is the creator of JavaScript! ` + emoticon.flat().join('')
);
Save this code to a file called index.js and run it from your terminal using the command node index.js. You should see Brendan Eich is the creator of JavaScript! ┌(˘⌣˘)ʃ output to the terminal.

Introducing npm, the JavaScript Package Manager
As I mentioned earlier, Node comes bundled with a package manager called npm. To check which version you have installed on your system, type npm -v.

In addition to being the package manager for JavaScript, npm is also the world’s largest software registry. There are over 1,000,000 packages of JavaScript code available to download, with billions of downloads per week. Let’s take a quick look at how we would use npm to install a package.

Installing a Package Globally
Open your terminal and type the following:

npm install -g jshint
This will install the jshint package globally on your system. We can use it to lint the index.js file from the previous example:

jshint index.js
You should now see a number of ES6-related errors. If you want to fix them up, add /* jshint esversion: 6 */ to the top of the index.js file, re-run the command and linting should pass.


If you’d like a refresher on linting, see A Comparison of JavaScript Linting Tools.

Installing a Package Locally
We can also install packages locally to a project, as opposed to globally, on our system. Create a test folder and open a terminal in that directory. Next type this:

npm init -y
This will create and auto-populate a package.json file in the same folder. Next, use npm to install the lodash package and save it as a project dependency:

npm install lodash --save
Create a file named test.js and add the following:

const _ = require('lodash');

const arr = [0, 1, false, 2, '', 3];
console.log(_.compact(arr));
Finally, run the script using node test.js. You should see [ 1, 2, 3 ] output to the terminal.

Working with the package.json File
If you look at the contents of the test directory, you’ll notice a folder entitled node_modules. This is where npm has saved lodash and any libraries that lodash depends on. The node_modules folder shouldn’t be checked in to version control, and can, in fact, be re-created at any time by running npm install from within the project’s root.

If you open the package.json file, you’ll see lodash listed under the dependencies field. By specifying your project’s dependencies in this way, you allow any developer anywhere to clone your project and use npm to install whatever packages it needs to run.

If you’d like to find out more about npm, be sure to read our article A Beginner’s Guide to npm — the Node Package Manager.

What Is Node.js Used For?
Now that we know what Node and npm are and how to install them, we can turn our attention to the first of their common uses: installing (via npm) and running (via Node) various build tools — designed to automate the process of developing a modern JavaScript application.

These build tools come in all shapes and sizes, and you won’t get far in a modern JavaScript landscape without bumping into them. They can be used for anything from bundling your JavaScript files and dependencies into static assets, to running tests, or automatic code linting and style checking.

We have a wide range of articles covering build tooling on SitePoint. Here’s a short selection of my favorites:

A Beginner’s Guide to Webpack
Up and Running with ESLint — the Pluggable JavaScript Linter
An Introduction to Gulp.js
Unit Test Your JavaScript Using Mocha and Chai
And if you want to start developing apps with any modern JavaScript framework (for example, React or Angular), you’ll be expected to have a working knowledge of Node and npm (or maybe Yarn). This isn’t because you need a Node back end to run these frameworks. You don’t. Rather, it’s because these frameworks (and many, many related packages) are all available via npm and rely on Node to create a sensible development environment in which they can run.

If you’re interested in finding out what role Node plays in a modern JavaScript app, read The Anatomy of a Modern JavaScript Application.


Node.js Lets Us Run JavaScript on the Server
Next we come to one of the biggest use cases for Node.js — running JavaScript on the server. This isn’t a new concept, and was first attempted by Netscape way back in 1994. Node.js, however, is the first implementation to gain any real traction, and it provides some unique benefits, compared to traditional languages. Node now plays a critical role in the technology stack of many high-profile companies. Let’s have a look at what those benefits are.

The Node.js Execution Model
In very simplistic terms, when you connect to a traditional server, such as Apache, it will spawn a new thread to handle the request. In a language such as PHP or Ruby, any subsequent I/O operations (for example, interacting with a database) block the execution of your code until the operation has completed. That is, the server has to wait for the database lookup to complete before it can move on to processing the result. If new requests come in while this is happening, the server will spawn new threads to deal with them. This is potentially inefficient, as a large number of threads can cause a system to become sluggish — and, in the worst case, for the site to go down. The most common way to support more connections is to add more servers.

Node.js, however, is single-threaded. It’s also event-driven, which means that everything that happens in Node is in reaction to an event. For example, when a new request comes in (one kind of event) the server will start processing it. If it then encounters a blocking I/O operation, instead of waiting for this to complete, it will register a callback before continuing to process the next event. When the I/O operation has finished (another kind of event), the server will execute the callback and continue working on the original request. Under the hood, Node uses the libuv library to implement this asynchronous (that is, non-blocking) behavior.

Node’s execution model causes the server very little overhead, and consequently it’s capable of handling a large number of simultaneous connections. The traditional approach to scaling a Node app is to clone it and have the cloned instances share the workload. Node.js even has a built-in module to help you implement a cloning strategy on a single server.

The following image depicts Node’s execution model:

Node’s execution model

Source: Introduction To Node.js by Prof. Christian Maderazo, James Santos

Or, if you prefer videos, check out this awesome talk: What the heck is the event loop anyway? It’s not Node-specific, but does a great job of explaining the concept.

Are There Any Downsides?
The fact that Node runs in a single thread does impose some limitations. For example, blocking I/O calls should be avoided, CPU-intensive operations should be handed off to a worker thread, and errors should always be handled correctly for fear of crashing the entire process.

Some developers also dislike the callback-based style of coding that JavaScript imposes (so much so that there’s even a site dedicated to the horrors of writing asynchronous JavaScript). But with the arrival of native Promises, followed closely by async await, flow control in modern JavaScript has become easier than it ever was.

“Hello, World!” — Server Version
Let’s have a quick look at a “Hello, World!” example HTTP server:

const http = require('http');

http.createServer((request, response) => {
  response.writeHead(200);
  response.end('Hello, World!');
}).listen(3000);

console.log('Server running on http://localhost:3000');
To run this, copy the code into a file named hello-world-server.js and run it using node hello-world-server.js. Open up a browser and navigate to http://localhost:3000 to see “Hello, World!” displayed in the browser.

Now let’s have a look at the code.


We start by requiring Node’s native HTTP module. We then use its createServer method to create a new web server object, to which we pass an anonymous function. This function will be invoked for every new connection that’s made to the server.

The anonymous function is called with two arguments (request and response). These contain the request from the user and the response, which we use to send back a 200 HTTP status code, along with our “Hello World!” message.

Finally, we tell the server to listen for incoming requests on port 3000, and output a message to the terminal to let us know it’s running.

Obviously, there’s a lot more to creating even a simple server in Node (for example, it’s important to handle errors correctly), so I’d advise you to check the documentation or consult our tutorial if you’d like to find out more.

What Kind of Apps Is Node.js Suited To?
Node is particularly suited to building applications that require some form of real-time interaction or collaboration — for example, chat sites, or apps such as CodeShare, where you can watch a document being edited live by someone else. It’s also a good fit for building APIs where you’re handling lots of requests that are I/O driven (such as those needing to perform operations on a database), or for sites involving data streaming, as Node makes it possible to process files while they’re still being uploaded. If this real-time aspect of Node is something you’d like to look into more, check out our tutorial on Building a Real-time Chat App.

Yet saying this, not everyone is going to be building the next Trello or the next Google Docs, and really, there’s no reason that you can’t use Node to build a simple CRUD app. However, if you follow this route, you’ll soon find out that Node is pretty bare-bones and that the way you build and structure the app is left very much up to you. There are various frameworks you can use to reduce the boilerplate, with Express having established itself as the front runner. Yet even a solution such as Express is minimal, meaning that if you want to do anything slightly out of the ordinary, you’ll need to pull in additional modules from npm. This is in stark contrast to frameworks such as Rails or Laravel, which come with a lot of functionality out of the box.

If you’d like to look at building a basic, more traditional app, check out our tutorial How to Build and Structure a Node.js MVC Application.

What Are the Advantages of Node.js?
Aside from speed and scalability, an often-touted advantage of using JavaScript on a web server — as well as in the browser — is that your brain no longer needs to switch modes. You can do everything in the same language, which, as a developer, makes you more productive (and hopefully, happier). For example, you can easily share code between the server and the client.

Another of Node’s big pluses is that it speaks JSON. JSON is probably the most important data exchange format on the Web, and the lingua franca for interacting with object databases (such as MongoDB). JSON is ideally suited for consumption by a JavaScript program, meaning that when you’re working with Node, data can flow neatly between layers without the need for reformatting. You can have one syntax from browser to server to database.

Finally, JavaScript is ubiquitous: most of us are familiar with JavaScript, or have used it at some point. This means that transitioning to Node development is potentially easier than to other server-side languages. To quote Craig Buckler in his Node vs PHP Smackdown, JavaScript might remain the world’s most misunderstood language — but, once the concepts click, it makes other languages seem cumbersome.

Other Uses of Node
And it doesn’t stop at the server. There are many other exciting and varied uses of Node.js!

For example it can be used as a scripting language to automate repetitive or error prone tasks on your PC. It can also be used to write your own command line tool, such as this Yeoman-Style generator to scaffold out new projects.

Node.js can also can be used to build cross-platform desktop apps and even to create your own robots. What’s not to love?

Conclusion
JavaScript is everywhere, and Node is a vast and expansive subject. Nonetheless, I hope that in this article I’ve offered you the beginner-friendly, high-level look at Node.js and its main paradigms that I promised at the beginning. I also hope that when you re-read the definitions we looked at previously, things will make a lot more sense.

Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.
