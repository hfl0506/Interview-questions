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
51. What is the difference between browser global scope and Node.js global scope ?
    - At global scope, `var` creates a property on the global object, which you can access via the `window` global, via `this` at global scope, or via `this` in a loose-mode function you call without doing anything specific to set `this`. Your call to `fn` above is that last category: a loose-mode function called without setting `this`.
    - But at Node.js module scope, `var` just creates a `var` in the module, it doesn't create a global or a property on the global object. It's like doing this:
    ```js
    (function () {
      // The wrapper Node.js provides node-style modules
      // This is "module" scope
      var foo = 10;
      function fn() {
        console.log(this.foo);
      }
      fn();
    })();
    ```
    - You can also use module scope on modern browsers, including Chrome, via type="module" on the script tag. But since JavaScript standard modules are always in strict mode, the this inside the call to fn would be undefined, causing an error:
    ```js
    <script type="module">
    var length = 10;
    function fn () {
      console.log(this);        // undefined
      console.log(this.length); // TypeError
    }
    fn();
    </script>
    ```
52. How to use `global` variable in Node.js ?
    - you can do below pratice for global:
    ```js
    //logger.js
    module.exports = new logger(customConfig);
    // foobar.js
    var logger = require("./logger");
    logger("barfoo");
    // alternative
    global.logger = new logger(customConfig);
    ```
53. When would you use global variables in Node.js ? Are they always bad ?
    - Global variables are considered an anti-pattern in almost any programming language because they make it very hard to follow and debug code.
    - When you browse the code, you never know which function sets or uses a global variable. When all variables are either local or passed to a function, you can be sure that the side-effects of the function are limited.
    - Global variables work at a distance. Screwing with the value of a global could have unexpected effects in a completely different part of the application. When you debug an error caused by that, you will have a very hard time finding out where the variable was changed to a wrong value.
    - Global variables share a namespace, so you can inadvertently reuse them although you don't intend to do so.
    - It's hard to tell how important a global variable is. You never know if it's used by just two functions or if its value is important all over the place.
54. What is the difference between `cluster` and `worker_threads` packages in Node.js ?
    - Clustering is a way to load-balance incoming requests to your nodejs server over several copies of that server.
    - Worker threads are a way for a single nodejs process to offload long-running functions to a separate thread, to avoid blocking its own main loop.
    - It depends on the problem you're solving. Worker threads are for long-running functions. Clustering makes a server able to handle more requests, by handling them in parallel. You can use both if you need to: have each nodejs cluster process use a worker thread for long-running functions.
55. Is there any difference between `res.send` and `return res.send` in Express.js ?

    - The return keyword returns from your function, thus ending its execution. This means that any lines of code after it will not be executed.
    - In some circumstances, you may want to use res.send and then do other stuff.

    ```js
    app.get("/", function (req, res) {
      res.send("i am a beautiful butterfly");
      // this logger will print
      console.log("this gets executed");
    });

    app.get("/", function (req, res) {
      return res.send("i am a beautiful butterfly");
      // this below logger will not print
      console.log("this does NOT get executed");
    });
    ```

56. What are `express.json()` and `express.urlencoded()` in Express.js ?
    - They are middleware function which is a piece of code that is called betweeen when a server gets a request from a client and when it sends a response back to the client.
    - They parse outgoing requests that both are used to parse data on `req` object. They only need when the request method is `POST` or `PUT`. Both used to part of `body-parser` in the express js.
    - `express.json()` and `express.urlencoded()` are helpful express middleware parser functions that let you parse outgoing request data depending on the encoding of data you're sending to the server.
57. How to gracefully shutdown Node.js server ?
    - Handle process kill signal
    - Stop new request from client
    - Close all data process
    - Exit from process
    ```js
    process.on("SIGTERM", () => {
      // handle process kill signal
      console.info("SIGTERM signal received.");
      console.log("Closing http server.");
      // stop new requests from client
      server.close(() => {
        console.log("Http server closed.");
        // close all data process
        mongoose.connection.close(false, () => {
          console.log("MongoDb connection closed.");
          // exit from process
          process.exit(0);
        });
      });
    });
    ```
58. Why to use `Buffer` instead of binary string to handle binary data ?
    - Pure javascript does not able to handle straight binary data very well. Since Node.js servers have to deal with TCP streams for reading and writing of data, binary strings will become problematic to work with as it is very slow and has a tendency to break. That's why it is always advisable to use Buffers instead of binary strings to handle binary data.
59. How the V8 engine works ?
    - Parsing: Javascript source code is parsed and converted to the Abstract syntax tree (AST). The code is broken down into tokens. Token is the building block of our code, anything that makes up the code. For example, let a = 5. Here let, a, =, 5 are tokens.
    - Compilation: Ignition generates an intermediate code called Byte code from the syntax tree.
    - Execution: Turbofan converts this byte code into highly optimized machine code. The machine code runs on the system.
    - ![image info](./../images/nodejs-59.png)
60. Does Node.js support multi-core platforms ?And is it capable of utilizing all the cores ?
    - Yes, Node.js would run on a multi-core system without any issue. But it is by default a single-threaded application, so it can't completely utilize the multi-core system.
    - However, Node.js can facilitate deployment on multi-core systems where it does use the additional hardware. It packages with a Cluster module which is capable of starting multiple Node.js worker processes that will share the same port.
61. Is it possible to use `Class` in Node.js ?

    - In the modern JavaScript, there is a more advanced “class” construct, that introduces great new features that are useful for object-oriented programming. As we can define a function in two way i.e. function expressions and function declarations.

    ```js
    // Class expression
    let class_name = class {
      constructor(method1, method2) {
        this.method1 = method1;
        this.method2 = method2;
      }
    };

    // Class declaration
    class class_name {
      constructor(method1, method2) {
        this.method1 = method1;
        this.method2 = method2;
      }
    }
    ```

62. What is LTS releases of Node.js why should you care ?
    - LTS release status is "long-term support", which typically guarantees that critical bugs will be fixed for a total of 30 months. Production applications should only use Active LTS or Maintenance LTS releases.
63. Is Node.js entirely based on a single-thread ?
    - Node JS Platform doesn’t follow the Multi-Threaded Request/Response Stateless Model. It follows the Single-Threaded with Event Loop Model. Node JS Processing model mainly inspired by JavaScript Event-based model with JavaScript callback mechanism. Because of which Node.js can handle more concurrent client requests with ease. The event loop is the heart of the Node.js processing model as shown below diagram.
    - ![image info](./../images/nodejs-63.png)
64. When not to use Node.js ?
    - Applications with heavy computing server-side. Since Node.js uses only one CPU core, heavy computations on the server will block all other requests. In this case, the event-driven non-blocking I/O model which is the strongest side of Node.js will become useless, and the application performance will suffer.
    - CRUD applications. In this case, using Node.js does not automatically mean poor performance. However, if you are building a simple CRUD app with data coming directly from the server and no API is needed, Node.js may be excessive, as its powerful features will be simply wasted.
    - Server-side web applications with relational databases. The reason for Node.js poor performance in this case is that its relational database tools are not as advanced as those created for other platforms. However, the recent news suggests that the latest version of Sequelize ORM may fill this gap and create the possibilities of using Node.js with relational databases.
65. What is Piping in Node ?
    - The readable.pipe() method in a Readable Stream is used to attach a Writable stream to the readable stream so that it consequently switches into flowing mode and then pushes all the data that it has to the attached Writable.
    ```js
    var fs = require("fs");
    var readable = fs.createReadStream("input.txt");
    var writable = fs.createWriteStream("output.txt");
    readable.pipe(writable);
    console.log("Program Ended");
    ```
66. What is the purpose of `__filename` variable in Node.js ?
    - `__filename` is little bit clear from its name that it is somewhere associated with the name of the file/code which we are executing. It returns the absolute path of the code file. The following approach covers how to implement `__filename` in the NodeJS project.
    ```jsx
    console.log("GeeksforGeeks");
    console.log("Name of the file which we" + " are currently executing is  ");
    console.log(__filename);
    ```
67. What's the difference between `dependecies`, `devDependencies` and `peerDependencies` in package.json file ?
    - dependencies are installed on both:
      1. `npm install` from a directory that contains `package.json`
      2. `npm install $package` on any other directory
    - `devDependencies` are:
      1. also installed on `npm install` on a directory that contains `package.json`, unless you pass the `--production` flag (go upvote Gayan Charith's answer), or if the `NODE_ENV=production` environment variable is set
      2. not installed on `npm install "$package"` on any other directory, unless you give it the `--dev` option.
      3. are not installed transitively.
    - `peerDependencies`:
      1. before 3.0: are always installed if missing, and raise an error if multiple incompatible versions of the dependency would be used by different dependencies.
      2. expected to start on 3.0 (untested): give a warning if missing on `npm install`, and you have to solve the dependency yourself manually. When running, if the dependency is missing, you get an error (mentioned by @nextgentech) This explains it nicely: https://flaviocopes.com/npm-peer-dependencies/
      3. in version 7 peerDependencies are automatically installed unless an upstream dependency conflict is present that cannot be automatically resolved
68. How would you handle errors for `async` code in Node.js ?
    - If we want to handle the error for asynchronous code in Node.js then we can do it in the following two manners.
      1. Handle error using callback: A callback function is to perform some operation after the function execution is completed. We can call our callback function after an asynchronous operation is completed. If there is some error we can call the callback function with that error otherwise we can call it with the error as null and the result of the asynchronous operation as the arguments.
      ```js
      const divide = (a, b, callback) => {
        setTimeout(() => {
          if (b == 0) {
            callback(new Error("Division by zero error"));
          } else {
            callback(null, a / b);
          }
        }, 1000);
      };
      ```
      2. Handle Promise rejection: Promise in Node.js is a way to handle asynchronous operations. Where we return a promise from an asynchronous function, it can later be consumed using then() method or async/await to get the final value. When we are using the then() method to consume the promise and we have to handle the promise rejections, then we can a catch() call to then() method call. Promise.catch() is a method that returns a promise and its job is to deal with rejected promise.
      ```js
      func()
        .then((res) => {
          // code logic
        })
        .catch((err) => {
          // promise rejection handling logic
        });
      ```
69. Can Node.js work without V8 ?
    - The current Node.js engine cannot work without V8. It would have no JavaScript engine and hence no ability to run any JavaScript code. The fact is that the native code bindings, which come with Node.js like the fs module and the Net module, rely on the V8 interface between C++ and JavaScript.
    - Although in the tech world everything is possible and Microsoft in July 2016, made an effort to use Chakra JavaScript engine (which was used in Edge browser at that time) in Node.js and replace the V8 engine, that project never took off and Microsoft Edge itself recently moved to Chromium, which uses V8 JavaScript engine.
    - The new kid on the block for server-side programming is DENO. Many consider that it could be a replacement to Node.js in the next 2-3 years, and it also uses V8 JavaScript engine under its hood.
70. What are `async` functions in Node ? Provide some examples.
    - An async function is a function declared with the `async` keyword, and the `await` keyword is permitted within it. The `async` and `await` keywords enable asynchronous, promise-based behavior to be written in a cleaner style, avoiding the need to explicitly configure promise chains.
    ```js
    function resolveAfter2Seconds() {
      return new Promise((resolve) => {
        setTimeout(() => {
          resolve("resolved");
        }, 2000);
      });
    }
    async function asyncCall() {
      console.log("calling");
      const result = await resolveAfter2Seconds();
      console.log(result);
      // expected output: "resolved"
    }
    asyncCall();
    ```
71. What are the Timing features of Node.js ?
    - The timer modules in Node.js consists of functions that help to control the timings of code execution. It includes `setTimeout()`, `setImmediate()`, and `setInterval()` methods.
      1. `setTimeout()`: The `setTimeout()` method is used to schedule code execution after a designated amount of milliseconds. The specified function will be executed once. We can use the `clearTimeout()` method to prevent the function from running. The `setTimeout()` method returns the ID that can be used in `clearTimeout()` method.
      2. `setImmediate()`:The `setImmediate()` method is used to execute code at the end of the current event loop cycle. Any function passed as the `setImmediate()` argument is a callback that can be executed in the next iteration of the event loop.
      3. `setInterval()`:The `setInterval()` method is used to call a function at specified intervals (in milliseconds). It is used to execute the function only once after a specified period.
         We can use the `clearInterval()` method to prevent the function from running. The `setInterval()` method returns the ID which can be used in `clearInterval()` method.
72. Explain usage of `NODE_ENV`.
    - Environment Variables: Before diving into NODE_ENV let us have some context about environment variables. An environment variable is a dynamic-named value that is typically used to provide the ability to configure the value into the code anonymously from outside. Simply speaking, an environment variable is a variable (key-value pair) whose value is set outside the program and its value can be used inside the code anonymously by using some mechanism. These environment variables that were set at the moment the process was started are hosted by the env property provided by the process core module of Node.js.
    ```
    USER_ID=239482
    KEY=foobar
    ```
    ```js
    // how to get env value
    process.env.USER_ID;
    process.env.KEY;
    ```
73. How does the `Cluster` module work ? What's the difference between it and a load balancer ?
    - The most basic clusters use a pair of redundant servers. More advanced clusters contain many other different machines, each connected and exchanging information about states and other resources. While it is technically possible for clusters to contain different types of nodes but performance reduces if the nodes are not identical. Some of the clusters available are High Availability Server Clusters, Load Balancing Clusters, High-Performance Clusters, and Storage Clusters.
    - Differences between cluster and load balancer:
      1. Load balancers distribute the process to different node base on the loading of it; Clusters combine a group of servers that run as a single entity for the process.
      2. Load balancers deploy with different types of servers simpler; Cluster requires identical servers within itself.
      3. Load balancers can operate independently of the destination servers and thus consumes fewer resources; Cluster modules require node managers and node agents to communicate within the cluster which occupies bandwidth and processing on the servers
      4. Relatively less resilient Load Balancing for applications eg.- While doing transactions If one server fails, the customer has to re-enter data again from the start as the user state will be lost; Server clusters are more resilient for applications eg.-If any server got failed during the transaction, another server within the cluster will work and the customer will complete the transaction.
74. When to use Synchronous vs Asynchronous code in Node.js ?
    - Asynchronous programming:
      1. should only be used in programming independent tasks, where it plays a critical role. For instance, asynchronous programs are ideal for development projects with a large number of iterations. Because steps don’t have to follow a fixed sequence, asynchronous programming keeps development moving forward.
      2. Responsive UI is a great use case for asynchronous planning. Take, for example, a shopping app. When a user pulls up their order, the font size should increase. Instead of first waiting to load the history and update the font size, asynchronous programming can make both actions happen simultaneously.
    - Synchronous programming:
      1. its code is easier to write and doesn’t require tracking and measuring process flows (as async does). Because tasks are dependent on each other, there’s a need to know if they could run independently without interrupting each other.
      2. Synchronous programming could be appropriate for a shopping app, for example. When checking out online, a user wants to buy all of their items together, not individually. Instead of completing an order every time the user adds something to their cart, synchronous programming ensures that the payment method and shipping destination for all items are selected at the same time.
75. Does JavaScript have a `map` function to iterate over an object properties ?
    - No. It doesn't but you could do below approach:
    ```js
    var myObject = { a: 1, b: 2, c: 3 };
    // returns a new object with the values at each key mapped using mapFn(value)
    function objectMap(object, mapFn) {
      return Object.keys(object).reduce(function (result, key) {
        result[key] = mapFn(object[key]);
        return result;
      }, {});
    }
    var newObject = objectMap(myObject, function (value) {
      return value * 2;
    });
    console.log(newObject);
    // => { 'a': 2, 'b': 4, 'c': 6 }
    console.log(myObject);
    // => { 'a': 1, 'b': 2, 'c': 3 }
    ```
76. When would you use `import * as X from "X"` ?
    - is asking for an object with all of the named exports of 'X'.
    ```js
    import * as X from "X";
    ```
    - is asking for the default export of X.
    ```js
    import X from "X";
    ```
77. How would you prevent Callback Hell without using promises, async or generators ?

    - spliting the callbacks into different functions

    ```js
    // before that
    const makeBurger = (nextStep) => {
      getBeef(function (beef) {
        cookBeef(beef, function (cookedBeef) {
          getBuns(function (buns) {
            putBeefBetweenBuns(buns, beef, function (burger) {
              nextStep(burger);
            });
          });
        });
      });
    };
    // after that
    const getBeef = (nextStep) => {
      const fridge = leftFright;
      const beef = getBeefFromFridge(fridge);
      nextStep(beef);
    };
    const cookBeef = (beef, nextStep) => {
      const workInProgress = putBeefinOven(beef);
      setTimeout(function () {
        nextStep(workInProgress);
      }, 1000 * 60 * 20);
    };
    ```

78. What is the difference between `pm2 restart` and `pm2 reload` ?
    - As opposed to restart, which kills and `restarts` the process, `reload` achieves a 0-second-downtime reload.
    - With `reload`, pm2 restarts all processes one by one, always keeping at least one process running.
    - If the reload system hasn’t managed to reload your application, a timeout will fallback to a classic restart.
79. What is the difference between `Cluster` and `Fork` mode in PM2 ?
    - The main difference between `fork_mode` and `cluster_mode` is that it orders pm2 to use either the child_process.fork api or the cluster api.
    - Fork mode: Take the `fork` mode as a basic process spawning. This allows to change the `exec_interpreter`, so that you can run a `php` or a `python` server with pm2. Yes, the `exec_interpreter` is the “command” used to start the child process. By default, pm2 will use `node` so that `pm2 start server.js` will do something like:
    ```js
    require("child_process").spawn("node", ["server.js"]);
    ```
    - This mode is very useful because it enables a lot of possibilities. For example, you could launch multiple servers on pre-established ports which will then be load-balanced by HAProxy or Nginx.
    - Cluster mode:The `cluster` will only work with `node` as it’s `exec_interpreter` because it will access to the nodejs cluster module (eg: `isMaster`, `fork` methods etc.). This is great for zero-configuration process management because the process will automatically be forked in multiple instances.
    - For example `pm2 start -i 4 server.js` will launch 4 instances of `server.js` and let the cluster module handle load balancing.
80. Compare PM2 Cluster Mode vs. Node.js Cluster module usage.
    - The cluster mode allows networked Node. js applications (http(s)/tcp/udp server) to be scaled across all CPUs available, without any code modifications. This greatly increases the performance and reliability of your applications, depending on the number of CPUs available. Under the hood, this uses the Node.
    - Node. js runs single threaded programming, which is very memory efficient, but to take advantage of computers multi-core systems, the Cluster module allows you to easily create child processes that each runs on their own single thread, to handle the load.
    - If your application is stateless then it is easy to use pm2 cluster mode as it does not require much effort (or no effort) in code changes. But if your application uses local data, sessions or using sockets then it is recommended to use Node.js inbuilt cluster module and start your application normally using pm2.
81. What is the difference between the child_prcoess `spawn` and `execute` functions in Node.js ?When to use each one ?
    - The main difference is the `spawn` is more suitable for long-running process with huge output. `spawn` streams input/output with child process. `exec` buffered output in a small (by default 200K) buffer. Also as I know `exec` first `spawn` subshell, then try to execute your process. To cut long story short use `spawn` in case you need a lot of data streamed from child process and `exec` if you need such features as shell pipes, redirects or even you need `exec` more than one program in one time.
82. What is the difference between `fork()` & `spawn()` in Node.js ?
    - Spawn is useful when you want to make a continuous data transfer in binary/encoding format — e.g. transferring a 1 Gigabyte video, image, or log file.
    - Fork is useful when you want to send individual messages — e.g. JSON or XML data messages.
83. Explain what is `Arrange-Act-Assert` pattern ?
    - Arrange/Act/Assert (AAA) is a pattern for arranging and formatting code in Unit Test methods. It is a best practice to author your tests in more natural and convenient way.
84. Compare `strict` vs `legacy` mode for Assert module in Node.js.
    - In strict assertion mode, non-strict methods behave like their corresponding strict methods. For example, `assert.deepEqual()` will behave like `assert.deepStrictEqual()`.
    - In strict assertion mode, error messages for objects display a diff. In legacy assertion mode, error messages for objects display the objects, often truncated.
    - Legacy assertion mode uses the == operator in:`assert.deepEqual()`, `assert.equal()`,`assert.notDeepEqual()`,`assert.notEqual()`.
    - Legacy assertion mode may have surprising results, especially when using `assert.deepEqual()`.
85. Is an `Event Emitter` synchronous or asynchronous ?
    - Yes, events are synchronous and blocking. They are implemented with simple function calls. If you look at the eventEmitter code, to send an event to all listeners, it literally just iterates through an array of listeners and calls each listener callback, one after the other.
86. List some differences between CommonJS module loader and ECMAScript module loader ?
    - The CommonJS module is executed at load time. Once a module is “Loaded Loading Loop”, only the part that has been executed will be output, and the part that has not been executed will not be output.
    - ES6 module is a dynamic reference. When encountering module loading command import, it does not execute the module, but generates a reference to the loaded module.
    - The CommonJS module specification is mainly applicable to the back-end Node. js, which is loaded synchronously, so the module has been executed when the module cycle is introduced. It is recommended that the module specification of ES6 be used in front-end project, and the syntax introduced by ES6 module is supported by installing Babel transcoding plug-in.
87. How can you have one global variable between all clustered workers in Node.js ?

    - below code as example:

    ```js
    cluster.on('message', (worker, msg, handle) => {
        if (msg.topic && msg.topic === INCREMENT) {
          // here we increment the counter
          counter++;
          for (const id in cluster.workers) {
            // Here we notify each worker of the updated value
            cluster.workers[id].send({
              topic: COUNTER,
              value: counter
            });
          }
        }
      });

    } else if (cluster.isWorker) {

      console.log(`Worker id: ${cluster.worker.id}`);
      // Here is a function that requests the counter be updated in the master from a worker.
      function incrementCounter() {
        process.send({ topic: INCREMENT });
      }

      // A dummy timeout to call the incrementCounter function
      setTimeout(incrementCounter, 1000 * cluster.worker.id);

      // Handle the counter update
      process.on('message', (msg) => {
        if (msg.topic && msg.topic === COUNTER) {
          console.log(`${cluster.worker.id}/${process.pid}: ${msg.topic} ${msg.value}`);
        }
      });

    }
    ```

88. Do I need Dependency Injection in Node.js and how to deal with it ?

    - you don't need a dependency injection container or service locater like you would in C#/Java. Since Node.js, leverages the module pattern, it's not necessary to perform constructor or property injection. Although you still can.
    - The great thing about JS is that you can modify just about anything to achieve what you want. This comes in handy when it comes to testing.
    - But you also can do it as below:

    ```js
    const User = require("./User");

    function UsersService(usersRepository) {
      async function getUsers() {
        return usersRepository.findAll();
      }

      async function addUser(userData) {
        const user = new User(userData);

        return usersRepository.addUser(user);
      }

      return {
        getUsers,
        addUser,
      };
    }

    module.exports = UsersService;
    ```

89. How does libuv work under the hood ?
    - libuv is a C library originally written for Node.js to abstract non-blocking I/O operations.
      1. Event-driven asynchronous I/O model is integrated.
      2. It allows the CPU and other resources to be used simultaneously while still performing I/O operations, thereby resulting in efficient use of resources and network.
      3. It facilitates an event-driven approach wherein I/O and other activities are performed using callback-based notifications.
    - If a program is querying the database, the CPU sits idle until the query is processed and the program stays at a halt, thereby causing wastage of system resources. To prevent this, libuv is used in Node.js which facilitates a non-blocking I/O.
    - It also has mechanisms to handle services like File System, DNS, network, child processes, pipes, signal handling, polling, and streaming.
    - To perform blocking operations that can’t be done asynchronously at OS level, libuv also includes a thread pool to distribute CPU loads.
90. Explain what is Reactor Pattern in Node.js ?
    - Reactor Pattern is used to avoid the blocking of the Input/Output operations. It provides us with a handler that is associated with I/O operations. When the I/O requests are to be generated, they get submitted to a demultiplexer, which handles concurrency in avoiding the blocking of the I/O mode and collects the requests in form of an event and queues those events.
      1. Blocking I/O: Application will make a function call and pause its execution at a point until the data is received. It is called as ‘Synchronous’.
      2. Non-Blocking I/O: Application will make a function call, and, without waiting for the results it continues its execution. It is called as ‘Asynchronous’.
    - Reactor Pattern comprises of:
      1. Resources: They are shared by multiple applications for I/O operations, generally slower in executions.
      2. Synchronous Event De-multiplexer/Event Notifier: This uses Event Loop for blocking on all resources. When a set of I/O operations completes, the Event De-multiplexer pushes the new events into the Event Queue.
      3. Event Loop and Event Queue: Event Queue queues up the new events that occurred along with its event-handler, pair.
      4. Request Handler/Application: This is, generally, the application that provides the handler to be executed for registered events on resources.
91. Can Node.js use other engines than V8 ?
    - No. The current node.js binary cannot work without V8. It would have no Javascript engine and thus no ability to run code which would obviously render it non-functional. Node.js was not designed to run with any other Javascript engine and, in fact, all the native code bindings that come with node.js (such as the fs module or the net module) all rely on the specific V8 interface between C++ and Javascript.
    - There is an effort by Microsoft to allow the Chakra Javascript engine (that's the engine in Edge) to be used with node.js. They build a V8 shim on top of Chakra so that the node.js binary code that expects to be talking to V8 can continue to do what it was doing, but actually end up talking to the Chakra engine underneath. From what I've read this is particularly targeted at Microsoft platforms that already have the Chakra engine and do not have the V8 engine running on them, though presumably you could use it on Windows too.
92. Why Node.js devs tend to lean towards the Module Requiring vs Dependency Injection ?
    - Due to many Nodejs devs might come from background of other object-oriented programming language, and D.I in their langauage is the best way to structure the service in web server. But there are also native Javascript devs switching to Node.js to become fullstack devs, and they prefer the CommonJS module way to structure the service, either they would not think D.I is only way to structure service. The main reason is Javascript related to dynamic language, both ways are suitable for it and it depends on experience.
93. How to solve `Process out of Memory Exception` in Node.js ?
    - This exception can be solved by increasing the default memory allocated to our program to the required memory by using the following command.
    ```
    node --max-old-space-size=<SPACE_REQD> index.js
    ```
    - SPACE_REQD: Pass the increased memory space (in Megabytes).
94. How would you scale Node application ?
    - `Microservice`:
      1. is another word for this scaling strategy. For practically you’ll be “juggling” with multiple microservices (although their size is of no significant importance, actually).
      2. Or multiple applications, with different codebases (and in many cases, each one of them has its own UI and dedicated database)
      3. And it’s by services and functionalities that you’ll be decomposing/scaling your Node.js app. A strategy that can lead to unexpected issues in the long run, but which, if implemented correctly, translates into clear gains for your apps’ performance.
    - `horizontal partitioning` or `sharding`:
      1. data partitioning calls for a lookup before you carry out each operation; this way you’ll identify the right instance of the application to be used.
      2. You might want to partition your Node.js app’s users by language or area of interest. In this case, a lookup step is a must; you’ll need to check that information, first things first.
    - `Cloning`:
      1. And this is the easiest strategy at hand for solving your “How to scale your Node.js app” dilemma!
      2. Just clone your Node.js back-end application, multiple times, and assign a specific part of the workload to each cloned instance!
      3. Node’s cluster module makes cloning on a single server ideally easy to implement!
95. What is the difference between `process.nextTick()` and `setImmediate()` ?
    - Use `setImmediate` if you want to queue the function behind whatever I/O event callbacks that are already in the event queue. Use `process.nextTick` to effectively queue the function at the head of the event queue so that it executes immediately after the current function completes.
    - So in a case where you're trying to break up a long running, CPU-bound job using recursion, you would now want to use `setImmediate` rather than `process.nextTick` to queue the next iteration as otherwise any I/O event callbacks wouldn't get the chance to run between iterations.
96. Explain some Error Handling approaches in Node.js you know about. Which one will you use ?

    - Using a try-catch block: The catch block handles any exception raised by the code in the try block.

    ```js
    try{
    const areYouAwesome = false;
    if(!areYouAwesome){
      throw new Error("We know you are awesome,
      we are having troubing with our code.")
      }
    }catch(error){
            console.log(error.message);
    }
    ```

    - Using try-catch while performing asynchronous operations: Asynchronous operations sometimes require the program to be halted while the data is retrieved. We can pair up async-await functions with try-catch blocks to handle errors.

    ```js
    const delay = (wait) => {
      return new Promise((resolve) => setTimeout(resolve, wait));
    };

    const awesomeFunction = async () => {
      try {
        await delay(2000);
        throw new Error("Error thrown after delay");
      } catch (error) {
        console.log(error.message);
      }
    };

    awesomeFunction();
    ```

    - Using Promises: Promises are used to handle asynchronous operations in JavaScript. They are three states for a promise namely the pending state, the resolved state, and the rejected state. In the pending state, the promise is waiting for some other function or for some data to be retrieved. In the resolved state, the function has worked as it’s intended and the promise is resolved. In the rejected state, some error has crept up in the function and the promise is rejected.

    ```js
    const awesomeFunction = (isAwesome) => {
        return new Promise((resolve, reject) => {
            if(isAwesome){
                resolve("You are awesome");
            }else{
                reject("We know you are awesome,
                      we are having troubing with our code.")
            }
        })
    }
    awesomeFunction(false).then((message) => {
    console.log(message);
    }).catch((error) => {
        console.log(error)
    });
    ```

    - Using an event listener: The process global object in Node.js can be used to listen for any uncaught exceptions that may have crept up in the program.

    ```js
    process.on('uncaughtException', error => {
    console.log(error.message);
    process.exit(1)
    })

    const awesomeFunction = (isAwesome) => {
        if(!isAwesome){
            throw new Error("We know you are awesome,
                        we are having troubing with our code.")
        }
    }
    awesomeFunction();
    ```

    - I would use try-catch block and async try-catch since these are modern way to write Javascript for personal project, if in work, I would follow the company code style to do so.

97. What is the purpose of using hidden classes in V8 ?
    - When you create a new object, the V8 engine will create a new hidden class for that. Then, if you modify that same object by adding a new property, the V8 engine will create a new hidden class with all the properties from the previous class and include the new property.
    - This hidden class concept not only allows you to bypass dictionary lookups; it also allows you to reuse already created classes when similar objects are created or modified.
98. Why do we need C++ Addons in Node.js ?
    - It gives the opportunity to make intensive, parallel, and high-accuracy calculations.
    - It also gives the opportunity to use C++ libraries in NodeJS.
    - We can integrate a third-party library written in C/C++ and use it directly in NodeJS.
    - The performance of C++ is far better on larger values or computation.
99. Why should you separate Express app and server ?
    - Data Abstraction and Encapsulation: While the server consists only of logic that deals with server configuration, setting up the middleware and initializing the routes, the app takes care of the application logic and abstracts the data model and business logic from the server layer. This ensures that the database/data is abstracted from the server layer and encapsulated by the application layer.
    - Modularity: By keeping the server and app functionalities separate, the code is divided into multiple modules, each having a single task or responsibility to perform. These can be individually used whenever required as there is a reduced dependency between modules. Duplicate code can be avoided through a clear separation of logic.
    - Scalability: Each individual component is assigned a unique responsibility. This allows changes to be made quickly without having to make changes everywhere in the code. For example, consider the logic of a module that is to be changed, which is being used as a submodule in several other functions. If the logic is a separate module, the change would only have to be made in that one module, instead of all the functions in which the usage of logic occurs.
    - Reusability: Since the application is divided into multiple modules that are assigned a single task, they can be reused in the application multiple times whenever the need be. For example, an application requiring the conversion of minutes into seconds multiple times might define this conversion as a separate function, to avoid the hassle of re-writing the logic throughout the application again and again.
100. What is V8 Templates ?

     - A template is a blueprint for Javascript funtions and objects. You can use a template to wrap C++ functions and data structures within Javascript objects. V8 has two types of templates:
     - Function Template is the blueprint for a single function. You create a Javascript instance of template by calling the template's GetFunction method from within the context in which you wish to iunstantiate the Javascript function. You can aslo associate a C++ callback with a function template which is called when the Javascript function instance is invoked.
     - Object Template is used to configure objects created with function template as their constructor. You can associate two types of C++ callbacks with object templates: accessor callback and interceptor callback. Accessor callback is invoked when a specific object property is accessed by script. Interceptor callback is invoked when any object property is accessed by script. In a nutshell, you can wrap C++ objects\structures within Javascript objects.

101. How V8 compiles Javascript code ?

     - Parsing Phase: During the parsing phase, the code is broken down into its respective tokens.
     - Compilation phase: Compilation is the process of converting human-readable code to machine code. There are two ways to compile the code :

       1. Using an Interpreter: The interpreter scans the code line by line and converts it into byte code. Example: Python
       2. Using a Compiler: The Compiler scans the entire document and compiles it into highly optimized byte code. Example: Java
       3. Unlike other languages, The V8 engine uses both a compiler and an interpreter and follows Just in Time(JIT) Compilation for improved performance.

     - Execution Phase: The byte code is executed by using the Memory heap and the Call Stack of the V8 engine’s runtime environment. Memory Heap is the place where all the variables and functions are assigned memory. Call Stack is the place where each individual functions, when called are pushed to the stack, and popped out after their execution. When the interpreter interprets the code, using an object structure, where the keys are the byte code and the values the functions which handle the corresponding byte code. The V8 engine orders the values in the form of a list in memory, which is saved into a Map thereby saving a lot of memory.

102. How many threads does Node actually create ?

     - Using Single thread and Concept of Event Loop: To overcome this problem, Node adopted a single thread system with event loop and asynchronous I/O operations. Using a single thread allows Node to execute one process at a time while the processes that take longer time than usual are handled by Node API and event loop. Event loop uses callbacks to return outputs from functions that were being handled by Node API and the tasks continue to execute normally till the whole code is processed.

103. Does JavaScript pass by references or pass by values

- JavaScript is always pass-by-value. This means everything in JavaScript is a value type and function arguments are always passed by value. That being said, object types are a bit more confusing.
- The confusion lies in the fact that object types are reference types which are passed by value. As weird as this sounds, a reference to an object is passed to a function by value. The subtle difference here lies in the fact that an object reference passed by value is not the same as passing an object by reference.

104.  What's the difference between `pm2` and `pm2-runtime` and when to use one ?

      - The main difference between pm2 and pm2-runtime is
        1. pm2-runtime designed for Docker container which keeps an application in the foreground which keep the container running,
        2. pm2 is designed for normal usage where you send or run the application in the background.

105.  Does the `cluster` in Node.js utilizes same event loop ?

      - When you use clustering in Node then you're running several Node processes.
      - Every Node process has its own event loop. All processes in the cluster can share the server ports but they don't actually share any state, and they don't share the event loops - every process has its own one.

106.  What is the difference between `cluster.fork()` vs `child_process.fork()` in Node.js ?

      - The difference between `cluster.fork()` and `child_process.fork()` is simply that cluster allows TCP servers to be shared between workers. `cluster.fork` is implemented on top of `child_process.fork`.

107.  How would you implement process communication when using `cluster` module in Node.js ?

- Cluster module lets you fork multiple child processes (using child_process.fork()). Making use of the events ‘online’, ‘disconnect’, ‘listening’, ‘message’, ‘error’ and ‘exit’ emitted by worker process, the state of worker process can be easily managed;
