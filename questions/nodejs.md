# Nodejs Interview Question

1. What npm is used for?
   - npm stands for Node Package Manager.
   - npm provides the following two main functionalities:
   - Online repositories for Node.js packages/modules which are searchable on search.nodejs.org
   - Command-line utility to install packages, do version management and dependency management of Node.js packages.
   - Another important use for npm is dependency management. When you have a node project with a package.json file,you can run npm install from the project root and npm will install all the dependencies listed in the package.json.
2. Explain the difference between local and global npm packages installation.

   - local packages are installed in the directory where you run npm install <package-name>,
     and they are put in the node_modules folder under this directory
   - global packages are all put in a single place in your system (exactly where depends on your setup),
     regardless of where you run npm install -g <package-name>

   In general, all packages should be installed locally.

   - This makes sure you can have dozens of applications in your computer, all running a different version of each package if needed.
   - Updating a global package would make all your projects use the new release, and as you can imagine this might cause nightmares in terms of maintenance, as some packages might break compatibility with further dependencies, and so on.

3. What is Callback?

   - A callback is a function called at the completion of given task; this prevents any blocking, and allows other code to be run in the meantime. Callbacks are the foundation of Node.js. Callbacks give you an interface with which to say, "and when you're done doing that, do all this."

   ```js
   const myCallback = (data) => {
     console.log(`got data: ${data}`);
   };

   const currentFunc = (callback) => {
     callback("get it?");
   };

   currentFunc(myCallback());
   ```

4. What are the key features of Node.js?
   - Asynchronous event driven IO helps concurrent request handling – All APIs of Node.js are asynchronous. This feature means that if a Node receives a request for some Input/Output operation, it will execute that operation in the background and continue with the processing of other requests. Thus it will not wait for the response from the previous requests.
   - Fast in Code execution – Node.js uses the V8 JavaScript Runtime engine, the one which is used by Google Chrome. Node has a wrapper over the JavaScript engine which makes the runtime engine much faster and hence processing of requests within Node.js also become faster.
   - Single Threaded but Highly Scalable – Node.js uses a single thread model for event looping. The response from these events may or may not reach the server immediately. However, this does not block other operations. Thus making Node.js highly scalable. Traditional servers create limited threads to handle requests while Node.js creates a single thread that provides service to much larger numbers of such requests.
   - Node.js library uses JavaScript – This is another important aspect of Node.js from the developer’s point of view. The majority of developers are already well-versed in JavaScript. Hence, development in Node.js becomes easier for a developer who knows JavaScript.
   - Active and vibrant community for the Node.js framework – The active community always keeps the framework updated with the latest trends in the web development.
   - No Buffering - Nodejs applications never buffer any data. They simply output the data in chunks.
5. Why does Node.js prefer Error-First Callback?
   - The usual pattern is that the callback is invoked as callback(err, result), where only one of err and result is non-null, depending on whether the operation succeeded or failed. Without this convention, developers would have to maintain different signatures and APIs, without knowing where to place the error in the arguments array.
   ```js
   fs.readFile(filePath, function (err, data) {
     if (err) {
       // error handling
     }
     // return data
   });
   ```
6. What do you mean by Asynchronous API?
   - All APIs of Node.js library are aynchronous that is non-blocking. It essentially means a Node.js based server never waits for a API to return data. Server moves to next API after calling it and a notification mechanism of Events of Node.js helps server to get response from the previous API call.
7. What are the benefits of using Node.js?
   - Aynchronous and Event Driven - All APIs of Node.js library are aynchronous that is non-blocking. It essentially means a Node.js based server never waits for a API to return data. Server moves to next API after calling it and a nitification mechanism of Events of Node.js helps server to get response from the previous API call.
   - Fast - Being built on Google Chrome's V8 Javascript Engine, Nodejs library is very fast in code execution.
   - Single Threaded but highly Scalable - Node.js uses a single threaded model with event looping. Event mechanism helps server to respond in a non-blocking ways and makes server highly scalable as opposed to tranditional servers with create limited threads to handle requests. Node.js uses a single threaded program and same program can services much larger number of requests than traditional server like Apache HTTP Server.
   - No Buffering - Node.js applications never buffer any data. These applications simply output the data in chunks.
8. What is Callback Hell and what is main cause of it?
   - asynchronous Javascript, or Javascript that uses callbacks, is hard to get right intuitively. A lot of code ends up looking like this:
   ```js
   fs.readdir(source, function (err, files) {
     if (err) {
       console.log("Error finding files: " + err);
     } else {
       files.forEach(function (filename, fileIndex) {
         console.log(filename);
         gm(source + filename).size(function (err, values) {
           if (err) {
             console.log("Error identifying file size: " + err);
           } else {
             console.log(filename + " : " + values);
             aspect = values.width / values.height;
             widths.forEach(
               function (width, widthIndex) {
                 height = Math.round(width / aspect);
                 console.log(
                   "resizing " + filename + "to " + height + "x" + height
                 );
                 this.resize(width, height).write(
                   dest + "w" + width + "_" + filename,
                   function (err) {
                     if (err) console.log("Error writing file: " + err);
                   }
                 );
               }.bind(this)
             );
           }
         });
       });
     }
   });
   ```
9. What is the difference between returning a callback and just calling a callback?

   ```js
   return callback();
   // the rest of code after return, will not execute

   callback();
   // the rest of codes will execute
   ```

   Of course returning will help the context calling async function get the value returned by callback.

   ```js
   function do2(callback) {
     log.trace("Execute function: do2");
     return callback("do2 callback param");
   }

   var do2Result = do2((param) => {
     log.trace(`print ${param}`);
     return `return from callback(${param})`; // we could use that return
   });

   log.trace(`print ${do2Result}`);
   ```

   Output:

   ```
   C:\Work\Node>node --use-strict main.js
   [0] Execute function: do2
   [0] print do2 callback param
   [0] print return from callback(do2 callback param)
   ```

10. What is libuv?
    - libuv is a C library that is used to abstract non-blocking I/O operations to a consistent interface across all supported platforms.
    - It provides mechanisms to handle file system, DNS, network, child processes, pipes, signal handling, polling and streaming.
    - It also includes a thread pool for offloading work for some things that can't be done asynchronously at the operating system level.
11. What is V8?
    The V8 library provides Node.js with a Javascript engine (a program that converts Javascript code into lower level or machine code that microprocessors can understand), which Node.js controls via the V8 C++ API. V8 is maintained by Google, for use in Chrome.

    The Chrome V8 engine:

    - The V8 engine is written in C++ and used in Chrome and Nodejs.
    - It implements ECMAScript as specified in ECMA-262.
    - The V8 engine can run standalone we can embed it with our own C++ program.

12. What is the file package.json?
    All npm packages contain a file, usually in the project root, called package.json - this file holds various metadata relevant to the project. This file is used to give information to npm that allows it to identify the project as well as handle the project's dependencies. It can also contain other metadata such as a project description, the version of the project in a particular distribution, license information, even configuration data - all of which can be vital to both npm and to the end users of the package. The package.json file is normally located at the root directory of a Node.js project.
    Here is an example of package.json

    ```json
    {
      "name": "your project name",
      "version": "0.1.0",
      "private": true,
      "scripts": {
        // script to run, build, test the project
      },
      "dependencies": {
        // dependencies which needs for the project, and will exist at production build
      },
      "devDependencies": {
        // dependencies which needs for the project, and will not exist at production build, only at dev environment
      }
    }
    ```

13. Name some Built-in Globals in Node.js
    Node.js has a number of built-in global identifiers that every Node.js developer should have some familiarity with. Some of these are true globals, being visible everywhere; others exist at the module level, but are inherent to every module, thus being pseudo-globals.

    globals(truly golbal env):

    - global - The global namespace. Setting a property to this namespace makes it globally visible within the running process.
    - process - The Node.js built-in process module, which provides interaction with the current Node.js process. <a href="https://nodejs.org/en/knowledge/getting-started/the-process-module/">Read More</a>
    - console - The Node.js built-in console module, which wraps various STDIO functionality in a browser-like way.<a href="https://nodejs.org/en/knowledge/getting-started/the-console-module/">Read More</a>
    - setTimeout(), clearTimeout(), setInterval(), clearInterval() - The built-in timer functions are globals.<a href="https://nodejs.org/en/knowledge/javascript-conventions/what-are-the-built-in-timer-functions/">Read More</a>

    pseduo-globals(exists at module level):

    - module, module.exports, exports - These objects all pertain to the Node.js module system.<a href="https://nodejs.org/en/knowledge/getting-started/what-is-require/">Read More</a>
    - **filename - The **filename keyword contains the path of the currently executing file. Note that this is not defined while running the <a href="https://nodejs.org/en/knowledge/REPL/how-to-use-nodejs-repl/">Node.js REPL</a>
    - **dirname - Like **filename, the **dirname keyword contains the path to the root directory of the currently executing script.Also not present in the <a href="https://nodejs.org/api/modules.html#**dirname">Node.js REPL</a>
    - require() - The require() function is a built-in function, exposed per-module, that allows other valid modules to be included.<a href="https://nodejs.org/en/knowledge/getting-started/what-is-require/">Read More</a>

14. What does Promisifying technique mean in Node.js?
    This technique is a way to be able to use a classic Javascript function that takes a callback, and have it return a promise:
    For example:

    ```js
    const fs = require("fs");

    const getFile = (fileName) => {
      return new Promise((resolve, reject) => {
        fs.readFile(fileName, (err, data) => {
          if (err) {
            reject(err);
            return;
          }
          resolve(data);
        });
      });
    };
    getFile("/etc/passwd")
      .then((data) => console.log(data))
      .catch((err) => console.log(err));
    ```

15. What's the difference between process.cwd() vs \_\_dirname ?

    - cwd is a method of global object process, returns a string value which is the current working directory of the Node.js process.
    - **dirname is the directory name of the current script as a string value. **dirname is not actually global but rather local to each module.

    ```
    Project
    ├── main.js
    └──lib
        └── script.js
    ```

    Suppose we have a file script.js files inside a sub directory of project, i.e. C:/Project/lib/script.js and running node main.js which require script.

    main.js

    ```js
    require("./lib/script.js");
    console.log(process.cwd());
    // C:\Project
    console.log(__dirname);
    // C:\Project
    console.log(__dirname === process.cwd());
    // true
    ```

    script.js

    ```js
    console.log(process.cwd());
    // C:\Project
    console.log(__dirname);
    // C:\Project\lib
    console.log(__dirname === process.cwd());
    // false
    ```

16. Why we always require modules at the top if a file? Can we require modules inside of functions?
    Yes, but shall never do it.

    Node.js always runs require synchronously. If you require an external module from within functions your module will be synchronously loaded when those functions run and this can cause two problems:

    - if that module is only needed in one route handler function it might take some time for the module to load synchronously. As a result, several users would be unable to get any access to your server and requests will queue up.
    - if the module you require causes an error and crashes the server you may not know about the error.

17. What is the preferred method of resolving unhandled exceptions in Node.js?
    - Using try-catch block: We know that Node.js is a platform built on JavaScript runtime for easily building fast and scalable network applications. Being part of JavaScript, we know that the most prominent way to handle the exception is we can have try and catch block.
    ```js
    try {
      // do some logic
    } catch (error) {
      // error handling
    }
    ```
    - Using Process: A good practice says, you should use Process to handle exception. A process is a global object that provides information about the current Node.js process. The process is a listener function that is always listening to the events.
    ```js
    process.on("uncaughtException", function (err) {
      console.log("Caught exception: " + err);
    });
    ```
18. Explain how does Nodejs work?
    Nodejs basically works on two concept which are non-blocking i/o and asynchronous.

    - Non-blocking I/O: Non-blocking i/o means working with multiple requests without blocking the thread for a single request. I/O basically interacts with external systems such as files, databases. Node.js not used for CPU-intersive work means for calculations, video processing because a single thread cannot handle the CPU works.

    - Asynchronous: Asynchronous is executing a callback function. The moment we get the response from the other server or database it will execute a callback function. Callback functions are called as soon as some work is finished and this is because the node.js uses an event-driven architecture. The single thread doesn’t work with the request instead it sends the request to another system which resolves the request and it is accessible for another request.

    To implement the concept of the system to handle the request node.js uses the concept of Libuv.

    Libuv is an open-source library built-in C. It has a strong focus on asynchronous and I/O, this gives node access to the underlying computer operating system, file system, and networking.

    - Event loop
    - Thread pool

    Event loop:
    The event loop contains a single thread and is responsible for handling easy tasks like executing callbacks and network I/O. When the program is to initialize all the top-level code is executed, the code is not in the callback function. All the applications code that is inside callback functions will run in the event loop. EventLoop is the heart of node.js. When we start our node application the event loop starts running right away. Most of the work is done in the event loop.

    Nodejs use event-driven-architecture.

    - Events are emitted.
    - Event loop picks them up.
    - Callbacks are called.

    Event queue: As soon as the request is sent the thread places the request into a queue. It is known as an event queue. The process like app receiving HTTP request or server or a timer will emit event as soon as they are done with the work and event loop will pick up these events and call the callback functions that are associated with each event and response is sent to the client.

    The event loop is an indefinite loop that continously receives the request and processes them. It checks the queue and waits for the incoming request indefinitely.

    Thread pool: Though node.js is single-threaded it internally maintains a thread pool. When non-blocking requests are accepted there are processed in an event loop, but while accepting blocking requests it checks for available threads in a thread pool, assigns a thread to the client's request which is then processed and send back to the event loop, and response is sent to the respective client.

19. What is Stream Chaining in Node.js?

    - Chaining is a mechanism to connect the output of one stream to another stream and create a chain of multiple stream operations.
    - It is normally used with piping operations. Now we'll use piping and chaining to first compress a file and then decompress the same.

    ```js
    const fs = require("fs");
    const zlib = require("zlib");

    // Compress the file input.txt to input.txt.gz
    fs.createReadStream("input.txt")
      .pipe(zlib.createGzip())
      .pipe(fs.createWriteStream("input.txt.gz"));

    console.log("File Compressed.");
    ```

20. What are Event Emitters?

    - EventEmitter is a class that helps to create a publisher-subscriber pattern in Nodejs.
    - At event emitter, can simply raise a new event from different part of application, and listener will listen to the raised event and have some action performed for event

    ```js
    import { EventEmitter } from "events";

    const eventEmitter1 = new EventEmitter();
    eventEmitter1.on("myEvent", () => {
      console.log("Listener");
    });

    const eventEmitter2 = new EventEmitter();
    eventEmitter2.emit("myEvent");
    ```

21. What Are Buffer and Why to use them in node.js ?
    - Buffer Class in Node.js is used to perform operations on raw binary data. Generally, Buffer refers to the particular memory location in memory. Buffer is very similar with array, but the difference between is Buffer only deal with binary data and could not resize.
    - The reason of using Buffer is necessary to deal with binary data, usually it related to TCP stream and performing a read-write operation on the file system.
22. What is Blocking Code in Node.js ?
    - Blocking is when the execution of additional Javascript in the Node.js process must wait until a non-Javascript operation completes. This happens because the event loop is unable to continue running Javascript while a blocking operation is occuring.
    - All of the I/O methods in the Node.js standard library provide asynchronous version, which are non-blocking, and accept callback functions.
    ```js
    // blocking
    const fs = require("fs");
    const data = fs.readFileSync("/file.md"); // blocks here until file is read
    console.log(data);
    moreWork(); // will run after console.log
    // non-blocking
    const fs = require("fs");
    fs.readFile("/file.md", (err, data) => {
      if (err) throw err;
      console.log(data);
    });
    moreWork(); // will run before console.log
    ```
23. How does concurrency work in Node.js ?
    Nodejs is single threaded but it has asynchronous nature that helps it to possible to handle events concurrently. The fact is after nodejs run functions, it will threat these functions as events and put it on callstack. Each event on callstack will emit by its nature, if it could be execute, it will execute immediately, the entire process is non-blocking. Otherwise if events are ajax ,Web API and DOM, it will still "handle" it and pop out of the call stack then put it to event queue in first in first out principle. The callstack will get up these event once callstack is empty, and execute event one by one. To conclude, nodejs is event concurrently and non-blocking, it essentially is concurrent illustration.
24. What is stream and what are types of streams available in Node.js ?
    - streams are objects that let you read data from a source or write data to a destination in continuous fashion.
    - These are Readable, Writable, Duplex and Transform type of stream
      1. readable: stream which is used for read operation
      2. writable: stream which is used for write operation
      3. duplex: stream which used both for read and write
      4. transform: stream which similar with duplex and the output is computed based on input
    - Each type of stream is eventEmitter and there are data, end, error and finish event for it.
25. How does Node.js handle Child Threads ?
    - In general, Node.js is a single threaded process and doesn't expose the child threads or thread management methods. It could use spawn() for specified asynchronous I/O task and execute in the background, and usually not execute any JS code or hinder with the main event loop or include module called ChildProcess.
26. When should we use Node.js ?
    - API application:
      1. Nodejs runs on a single thread which makes it easier to handle up to 10,000 concurrent requests.
      2. All blocking I/O tasks for instance the database access and it handled by asynchronously by internal threads without interrupting the main thread
    - Real-time applications:
      Nodejs is good at building real-time applications like messaging, notification delivery, live streaming and collaboration tools.
      For example the messaging application, nodejs include great library for it, such as socket.io and webSocket.
    - Microservices:
      1. Nodejs assigns I/O tasks to the internal IO threads without blocking the main thread
      2. Nodejs uses event-driven architectures which can be highly decoupled.
27. What is the difference between setTimeout(fn, 0) vs setImmediate(fn) ?
    - setTimeout is simply like calling the function after delay has finished and it will not executed immediately.It will wait for all callstack job is done and it will execute, then take the latency and run.
    - setImmediate has different approach with setTimeout, it directly check event queue, and if there is nothing for waiting to do, it will execute immediately.
    - essentially setImmediate could be twice as fast than setTimeout.
28. What is the Event Loop ?
    - Event loop is something that pulls stuff out of the queue and places it onto function execution stack whenever the function stack becomes empty. The procedure of javascrpit handle event, first it will follow the first in last out principle to stack function on call stack, then some of the function will execute, and it will return depends on what attribute it is. The Web APIs, ajax, DOM function will emit then pass it to event queue as first in first out principle. The call stack will pull event in the queue once it empty the stack and it will execute until the queue is empty as well.
29. When should I use EventEmitter ?
    - The Event Emitter should be used when the same event can occur multiple times, or may not occur at all. A callback, in fact, is expected to be invoked exactly once, whether the operation is successful or not. Callback means call me when you are ready.
    - An API that uses callbacks can notify only one particular callback while using an EventEmitter allows us to register multiple listeners for the same event.
    - Use event emitter if you need to notify the user of a state change.
    - For testing purpose, if you want to make sure a function is called inside a function, emit an event.
30. What is event loop in Nodejs ?
    - Event loop is something that pulls stuff out of the queue and places it onto function execution stack whenever the function stack becomes empty. The procedure of javascrpit handle event, first it will follow the first in last out principle to stack function on call stack, then some of the function will execute, and it will return depends on what attribute it is. The Web APIs, ajax, DOM function will emit then pass it to event queue as first in first out principle. The call stack will pull event in the queue once it empty the stack and it will execute until the queue is empty as well.
31. What is difference between synchronous and asynchronous method of fs module ?
    - Synchronous methods: Synchronous functions block the execution of the program until the file operation is performed. These functions are also called blocking functions. For example, fs.readFileSync(), fs.writeFileSync()
    - Asynchronous methods: Asynchronous functions do not block the execution of the program and each command is executed after the previous command even if the previous command has not computed the result. The previous command runs in the background and loads the result once it has finished processing. Thus, these functions are called non-blocking functions. For example, fs.readFile(), fs.writeFile()
32. How to avoid Callback Hell in Node.js ?

    - To avoid callback hell, suppose to use Promises in javascript for handle asynchronous operation in Nodejs. It allow function to return value from an asynchronous fucntion like synchronous functions.

    ```js
    // from this
    const add = function (a, b, callback) {
      setTimeout(() => {
        callback(a + b);
      }, 2000);
    };

    add(1, 2, (sum1) => {
      add(3, sum1, (sum2) => {
        add(4, sum2, (sum3) => {
          console.log(`Sum of first 4 natural 
        numbers using callback is ${sum3}`);
        });
      });
    });
    // to this
    const addPromise = function (a, b) {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve(a + b);
        }, 2000);
      });
    };

    addPromise(1, 2)
      .then((sum1) => {
        return addPromise(3, sum1);
      })
      .then((sum2) => {
        return addPromise(4, sum2);
      })
      .then((sum3) => {
        console.log(
          `Sum of first 4 natural numbers using 
        promise and then() is ${sum3}`
        );
      });
    // modern and cleaner solution
    (async () => {
      const sum1 = await addPromise(1, 2);
      const sum2 = await addPromise(3, sum1);
      const sum3 = await addPromise(4, sum2);

      console.log(
        `Sum of first 4 natural numbers using 
        promise and async/await is ${sum3}`
      );
    })();
    ```

33. Could we run an external process with Nodejs ?
    Yes, it is possible and see below code.
    ```js
    // this
    var exec = require("child_process").exec;
    exec("pwd", function callback(error, stdout, stderr) {
      // result
    });
    // alternative
    const { exec } = require("child_process");
    exec("yourApp").unref();
    ```
34. Are you familiar with differences between Node.js modules and ES6 modules ?
    Nodejs Modules:
    - It is the builtin function and it is the easiest way to include modules that exist in separate files. The basic functionality of require is that it reads a JavaScript file, executes the file, and then proceeds to return the export object. It not only allows you to add built-in core Node modules but also community-based modules (node_modules), and local modules in the desired program. There are various inbuilt modules in a node like – HTTP module, URL module, query string module, path module and a lot more.
    ```js
    // commonJS module
    const express = require("express");
    ```
    ES6 Modules:
    - These statements are used to refer to an ES module. Other file types can’t be imported with these statements. They are permitted only in ES modules and the specifier of this statement can either be a URL-style relative path or a package name.
    ```js
    // import file
    import "./private-module.js";
    // export file
    module.exports = "A Computer Science Portal";
    ```
35. What are the use cases for the Nodejs vm core module ?
    - It can be used to safely execute a piece of code contained in a string or file. The execution is performed in a separate environment that by default has no access to the environment of the program that created it.
      \*p.s vm is not as safe as expected by running below code
    ```js
    vm.runInNewContext(
      "this.constructor.constructor('return process')().exit()"
    );
    ```
36. What is N-API in Nodejs ?
    - The N-API is a C API that ensures ABI stability across Node.js version and differet compile levels. N-API guarantees that it will always be backward compatible, it means a module created today and it will continue run on all future versions of Node.
    - N-API is ABI-stable, module will continue to run even without recompilation.
    - N-API make sure module create will run even the JS engine is changed.
37. What is the relationship between Nodejs and V8 ?
    - V8 is the javascript engine inside of nodejs that parses and runs your javascript. The same V8 engine is used of Chrome to run javascript in the Chrome browser. Google open-sourced the V8 engine and the builders of node.js used it to run Javascript in node.js.
38. Explain the concept of Domain in Nodejs
    - Domains provide a way to handle multiple different IO operations as a single group. If any of the event emitters or callbacks registered to a domain emit an "error" event, or throw an error, then the domain object will be notified, rather than losing the context of the error in the process.on("uncaughtException")handler, or causing the program to exit immediately with an error code.
39. Provide some of the reasons not to use Node.js
    - application with heavy computing server-side or CPU driven application, due to nodejs only uses one CPU core, heavy computations on the server will block all other request. The event-driven non-blocking I/O become useless and nodejs performance will suffer.
    - CRUD applications will not fully using nodejs power and its ability become not to shine in this senerio.
    - Application using relational database, due to relation database tooling have not optimize nodejs performance, therefore using relational database use cases is not great for nodejs.
40. What exactly does module.exports do in Node,js, and what would a simple example be ?
    - The module.exports is a special object which is included in every Javascript file in the Node.js application by default. The module is a variable that represents the current module, and exports is an object that will be exposed as a module.
    ```js
    // Message.js
    exports.SimpleMessage = "Hello World";
    // app.js
    const msg = require("./Message.js");
    console.log(msg.SimpleMessage);
    ```
41. What is the different between require(x) and ES6 import x in Nodejs ?
    - ES6 module are pre-parsed in order to resolve further imports before code is executed.
    - CommonJS module load dependencies on demand while executing the code.
42. What is export default in Javascript ?
    It is part of the ES6 module system. Named exports are useful to export several values. During the import, it is mandatory to import them within curly braces with the same name of the corresponding object.
    ```js
    export { myFunction as default };
    // export individual features as default
    export default function () { /* ... */ }
    export default class { .. }
    ```
43. Explain the order of Event Listeners execution in Node.js
    - Event handlers are always called in the order in which they were registered. Once registered, you cannot insert additional handlers ahead of them. Unless you are some how able to obtain a list of all the handlers, and their EventListener objects, and call removeEventListener to remove them, insert your own, and then reinsert the originals. In practice this is likely to be impossible.
44. Is an Event Emitter Synchronous or Asynchronous ?
    - The event emitter execute all callback in a synchronous manner. Every time you call a function, its context is pushed on the top of the call stack. When the function ends, the context is taken off from the stack. But it could operation as asynchronous mode using setImmediate() or process.nextTick(), and it will track the empty status of call stack, execute once call stack is empty.
45. How do I run a Nodejs app as a background aservice ?
    - Using forever tool. The forever is a simple Command Line Interface Tool that ensures that a given particular script runs continuously without any interaction.
    ```
    npm install forever -g
    ```
    ```
    forever start /<app_name>/index.js
    ```
    - The second method involves create a service file and manually starting the app and enabling the service to keep it running in the background.
    - Create a new file <app_name>.service file replacing <app_name> with the name of the node.js app. Inside the files, enter the following values:
    ```
    ExecStart=/var/www/<app_name>/app.js
    Restart=always
    User=nobody
    Group=nogroup
    Environment=PATH=/usr/bin:/usr/local/bin
    Environment=NODE_ENV=production
    WorkingDirectory=/var/www/<app_name>
    ```
    - After configuring the service file,Copy the <app_name>.service file into the /etc/systemd/system.
    - Start the app with the following command to make it run with the service file:
    ```
    systemctl start <app_name>
    ```
    - Another method which can be used to run a node.js app as a background by using nohup. The nohup is another Command Line Interface Tool which can be used to run a node.js app as a background service.
      Run the following command to start the nohup replacing the <app_name> with the name of the node.js app:
    ```
    nohup node /<app_name>/index.js &
    ```
46. What is the purpose of pm2 save ?
    - pm2 save takes a snapshot of your currently running Node applications. You can then restore these applications using pm2 resurrect.
    - This is useful because it means you don't have to manually restart each application when you restart pm2 (such as a machine reboot). Instead, you can just have a script that calls pm2 resurrect and it'll start up all the Node apps.
    - pm2 resurrect is useful to be called manually. If you want your processes to automatically start on boot, you should create a startup script with pm2 startup.
47. When would you use cluster module in Nodejs ?
    - The cluster module provides a way of creating child processes that runs simultaneously and share the same server port.
    - Node.js runs single threaded programming, which is very memory efficient, but to take advantage of computers multi-core systems, the Cluster module allows you to easily create child processes that each runs on their own single thread, to handle the load.
48. Which one is better: Nodejs built in cluster or PM2 clustering ?
    - stateless application prefer to use pm2 due to less or no effort in code changes.
    - using local data, sessions or sockets application recommended to use Nodejs built in cluster and start application normally with pm2.
49. What is the meaning of the @ prefix on npm package ?
    This is the feature of NPM called 'scoped packages', which allow NPM packages to be namespaced.
    - allow organizations to define the scope authority, for instance "@angular"
    - the common name would be used in scope of package, for instance "@angular/http"
50. What is the purpose of using assert module in Node.js ?
    The assert module provides a way of testing expressions. If the expression evaluates to 0, or false, an assertion failure is being caused, and the program is terminated and it is built-in module of nodejs.
