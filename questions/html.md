1. What is an iframe and how it works ?
   - An iframe is an HTML document which can be embedded inside another HTML page.
   ```html
   <iframe src="https://github.com" height="300px" width="300px"></iframe>
   ```
2. Explain meta tags in HTML

   - Meta tags always go inside head tag of the HTML page
   - Meta tags is always passed as name/value pairs
   - Meta tags are not displayed on the page but intended for the browser
   - Meta tags can contain information about character encoding, description, title of the document etc

   ```html
   <!DOCTYPE html>
   <html>
     <head>
       <meta name="description" content="I am a web page with description" />
       <title>Home Page</title>
     </head>
     <body></body>
   </html>
   ```

3. What is the purpose of the alt attribute on images ?
   - The alt attribute provides alternative information for an image if a user cannot view it. The alt attribute should be used to describe any images except those which only serve a decorative purposes, in which case it should be left empty.
4. What is the difference between span and div ?
   - div is block element
   - span is inline element
   - it is fine if inline element inside the block element, but it is not allow on the contrary
5. How can I get indexed better by search engines ?
   - It is possible to get indexed better by placing the following two statements in the <HEAD> part of your documents:
   ```html
   <meta name="keywords" content="keyword keyword keyword keyword" />
   <meta name="description" content="description of your site" />
   ```
   Both may contain up to 1022 characters. If a keyword is used more than 7 times, the keywords tag will be ignored altogether. Also, you cannot put markup (other than entities) in the description or keywords list.
6. What were some of the key goals and motivations for the HTML5 specification ?
   - Deliver rich content (graphics, movies, etc.) without the need for additional plugins, such as Flash.
   - Provide better semantic support for web page structure through new structural element tags.
   - Provide a stricter parsing standard to simplify error handling, ensure more consistent cross-browser behaviour, and simplify compatibility with documents written to older standards.
   - Provide better cross-platform support whether running on a PC, Tablet, or Smartphone.
7. How can you hightlight text in HTML ?
   - if you are working with an HTML5 page, the <mark> tag can be a quick and easy way of highlighting or marking text on a page:
   ```html
   <mark>highlighted text</mark>
   ```
   To highlight text with just HTML code and support for all browsers, set the background-color style, as shown in the example below, using the HTML tag.
   ```html
   <span style="background-color: #FFFF00">Yellow text.</span>
   ```
8. Briefly describe the correct usage of the following HTML5 semantic elements: `<header>, <article>, <section>, <footer>`
   - header is used to contain introductory and navigational information about a section of the page. This can include the section heading, the author's name, time and date of publication, table of contents, or other navigational information.
   - article is meant to house a self-contained composition that can logically be independently recreated outside of the page without losing it's meaning. Individual blog posts or news stories are good examples.
   - section is a flexible container for holding content that shares a common informational theme or purpose.
   - footer is used to hold information that should appear at the end of a section of content and contain additional information about the section. Author's name, copyright information, and related links are typical examples of such content.
9. What is Character Encoding ?
   - To display an HTML page correctly, a web browser must know which character set (character encoding) to use. This is specified in the tag:
   ```html
   // html4
   <meta http-equiv="Content-Type" content="text/html;charset=ISO-8859-1" />
   // html5
   <meta charset="UTF-8" />
   ```
10. What is a self closing tag ?
    - In HTML5 it is not strictly necessary to close certain HTML tags. The tags that aren't required to have specific closing tags are called "self closing" tags.
    - An example of self closing tag is something like a line break (<br />) or the meta tag (<meta>). This means that the following are both acceptable:
    ```html
    <meta charset="UTF-8" />
    ...
    <meta charset="UTF-8" />
    ```
11. What's the difference between an "attribute" and a "property" in HTML ?
    - Attributes are defined on the HTML markup but properties are defined on the DOM. To illustrate the difference, imagine we have this text field in our HTML: <input type="text" value="Hello">
    ```js
    const input = document.querySelector("input");
    console.log(input.getAttribute("value"));
    console.log(input.value); // hello
    // add World into value
    console.log(input.getAttribute("value"));
    console.log(input.value);
    ```
12. When is it appropriate to use the small element ?
    - The `<small>` HTML element represents side-comments and small print, like copyright and legal text, independent of its styled presentation. In general, it renders text within it one font-size smaller, such as from small to x-small.
13. Explain the difference between block elements and inline elements.
    - Block elements: They consume the entire width available irrespective of their sufficiency. They always start in a new line and have top and bottom margins. It does not contain any other elements next to it.
      etc:
      `<h1>-<h6>,<div>,<hr>,<li>,<ul>,<ol>,<p>,<table>,<header>,<nav>,<footer>,<main>,<section>,<article>,<aside>`
    - Inline elements: They occupy only enough width that is sufficient to it and allows other elements next to it which are inline. Inline elements don't start from a new line and don't have top and bottom margins as block elements have.
      etc:
      `<a>,<br>,<script>,<input>,<img>,<span>,<b>,<label>`
14. Explain almost standard, full standard and quirks mode
    - Quirks modes: Layout emulates non-standard behavior as supported by old browsers.
    - Almost standard modes: A small number of quirks/old behavior are supported while rendering the layout.
    - Full standard modes: Layout emulates standard behavior as described by HTML and CSS specifications.
15. How do you set IE compatibility mode ?
    - Select the Tools drop-down menu or the gear icon in Internet Explorer.
    - Select Compatibility View settings.
    - Modify the settings either to enable Compatibility View for a site or to disable Compatibility View. Click Close when you have finished making changes. ...
    - You're done!
16. What's new in HTML 5 ?

    - audio and video: these are two major addition of HTML 5. It allow developers to embed a video or audio on their website. HTML 5 vidoe can use CSS and CSS3 to style the video tag.

    ```html
    <video width="300" height="200" controls autoplay>
      <source src="/html5/foo.ogg" type="video/ogg" />
      <source src="/html5/foo.mp4" type="video/mp4" />
      Your browser does not support the video element.
    </video>

    <audio controls autoplay>
      <source src="/html5/audio.ogg" type="audio/ogg" />
      <source src="/html5/audio.wav" type="audio/wav" />
      Your browser does not support the audio element.
    </audio>
    ```

    - vector graphics: such as svg and circle it impacts use of Adobe Flash in website.

    ```html
    <svg id="svgelem" height="200" xmlns="http://www.abc.org/2000/svg">
      <circle id="redcircle" cx="50" cy="50" r="50" fill="red" />
    </svg>
    ```

    - header and footer: there is no longer a need to identify the two elements with a `<div>` tag. Footer is placed at the end of the web page while header is placed at the start of the web page. With this tag, browser will know load which one first.

    ```html
    <html>
      <head>
        <title>Header Tag</title>
      </head>
      <body>
        ...
      </body>
      <footer>This is footer</footer>
    </html>
    ```

    - figure and figcaption: html5 allows to use a <figure> element to mark up a photo in a document, and a <figcaption> element to define a caption for the photo.

    ```html
    <figure>
      <img
        src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/20190710102234/
                download3.png"
        alt="GFG"
        style="width:50%"
      />
      <figcaption>Fig.1 - Geeksforgeeks.</figcaption>
    </figure>
    ```

    - nav: it defines a set of navigation links, used for the part of an internet site that links to different pages at the website.

    ```html
    <nav>
      <a href="/html/">HTML</a>
      <a href="/css/">CSS</a>
      <a href="/js/">JavaScript</a>
      <a href="/jquery/">jQuery</a>
    </nav>
    ```

    - progress Tag: is used to check the progress of a task during the execution. Progress tag can be used with the conjunction of Javascript.

    ```html
    <progress id="file" value="32" max="100">32%</progress>
    ```

    - placeholder attribute: it specifies a short hint that describe the expected value of an input field/text area. The short hint is displayed in the field before the user enters a value.

    ```html
    <input type="text" name="fname" placeholder="first name" />
    ```

    - email attribute: when the input type in the form set as email, then the browser gets the instruction from the code to write a valid format email.

    ```html
    <input type="email" value="abc@gmail.com" />
    ```

    - storage: In the case of HTML, we can use the browser as the temporary storage whereas, in the case of HTML5, application cache, web SQL database, and web storage is used.
    - Ease of use: While HTML5 does have risks like constant updates, it is generally easy to keep up with the changes & updates because of simpler syntax as compared to other versions of HTML.

17. Have you used different HTML templating languages before ?
    - Yes, Pug (formerly Jade), ERB, Slim, Handlebars, Jinja, Liquid, and EJS just to name a few. In my opinion, they are more or less the same and provide similar functionality of escaping content and helpful filters for manipulating the data to be displayed. Most templating engines will also allow you to inject your own filters in the event you need custom processing before display.
18. How do you serve a page with content in multiple languages ?
    - Choosing the right language to serve, there are two options, either let user specify the preferred language explicitly or make your best guess based on existing data about user.
      1. Setting language explicitly: allow user to choose the language of the page is to include locale segment into the url.
         - Alternatively you can add some language selection mechanism that will store the picked language in current session, for example in cookies. So you'll be able to serve the localized version of your page, based on that information.
      2. Guessing language preference: There is special Accept-Language request header that you can use to get the language preference.
         This header has a list of locales with priorities, where default priority is 1.
      ```
      Accept-Language: fr-CH, fr;q=0.9, en;q=0.8, de;q=0.7, *;q=0.5
      ```
    - Providing language info for current page, there are few things can do about it:
      1. provide the charset for the html, due to browser will use default either `Latin-1` or `Windows-1252` in html 5,
         for example you could using `<meta charset="utf-8 />` tag.
      2. Also you could do this in html, to specify the lang.
      ```html
      <html lang="en"></html>
      ```
19. What is an optional tag?

    - Omit optional tags (optional). For file size optimization and scannability purposes, consider omitting optional tags. The HTML5 specification defines what tags can be omitted.

    ```html
    <!-- Google prefer-->
    <!DOCTYPE html>
    <title>Saving money, saving bytes</title>
    <p>Qed.</p>
    ```

    ```html
    <!-- W3Cschool prefer-->
    <!DOCTYPE html>
    <html>
      <title>Page Title</title>

      <body>
        <h1>This is a heading</h1>
        <p>This is a paragraph.</p>
      </body>
    </html>
    ```

20. How do you change the direction of html text ?
    - The HTML dir attribute is applied to HTML elements. For example, you can set the text direction of a textarea to right-to-left with the value rtl as follows:
    ```html
    <textarea dir="rtl"></textarea>
    <!-- Syntax -->
    <element dir="ltr|rtl|auto"></element>
    ```
    - There are `ltr`, `trl` and `auto` for the attribute values, ltr refer to left-to-right text direction and default,
      trl refer to right-to-left text direction and auto is Let the browser figure out the text direction, based on the content (only recommended if the text direction is unknown)
21. What are defer and async attributes on a `<script>` tag ?
    - `<script async>` are executed as soon as the script is loaded, so it doesn't guarantee the order of execution (a script you included at the end may execute before the first script file )
    - `<script defer>` are guarantees the order of execution in which they appear in the page.
22. What is the difference between `<section>` and `<div>` ?
    - `<section>` represents a generic section of a document or application. A section, in this context, is a thematic grouping of content. Each section should be identified, typically by including a heading(h1-h6 element) as a child of the `<section>` element.
    - `<div>` has no special meaning at all. It represents its children. It can be used with the class, lang, and title attributes to mark up semantics common to a group of consecutive elements.
23. Where and why is the rel="noopener" attribute used ?

    - use case:
      ```html
      <a href="https://www.example.com" rel="noreferrer">Link to Example.com</a>
      ```
    - The reason for using this especially useful when opening untrusted links, in order to ensure they cannot tamper with the originating document via the Window.opener property (see About rel=noopener for more details), while still providing the Referer HTTP header (unless noreferrer is used as well).

24. Can a web page contain multiple `<header>` elements ? What about `<footer>` elements ?

    - Yes, both `<header> and <footer>` can be added multiple times in a webpage. Both of these tags are designed to serve a crucial purpose in relation to their parent section. Not only the page `<body>` contains a header and a footer, but every `<section>` and `<article>` also contains these two, although the use of multiple footers is always not required.

25. What is WebSQL ?

    - Web SQL is a web page API for storing or managing the data in databases that can be queried using a variant of SQL like creating databases, opening the transaction, creating tables, inserting values to tables, deleting values, and reading data.
    - The Web SQL Database API is not a part of the HTML5 specification but it is a separate specification. It specifies a set of APIs to manipulate the client-side databases using SQL. The web SQL database works in the latest version of Safari, Google Chrome, Android browsers, and Opera.
    - examples methods: openDatabase, transaction, executeSql

    ```js
    var gfgDb = openDatabase("mydb", "1.0", "Test DB", 2 * 1024 * 1024);

    // create table
    gfgDb.transaction(function (tx) {
      tx.executeSql("CREATE TABLE IF NOT EXISTS CLASS (id unique, class)");
    });
    tx.executeSql('INSERT INTO CLASS (id, class) VALUES (1, "First")');
    tx.executeSql('INSERT INTO CLASS (id, class) VALUES (2, "Second")');
    ```

26. What is the DOM ?
    - The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content.
    - The DOM represents the document as nodes and objects; that way, programming languages can interact with the page.
    - A web page is a document that can be either displayed in the browser window or as the HTML source. In both cases, it is the same document but the Document Object Model (DOM) representation allows it to be manipulated.
    ```js
    // example of manipulate DOM by javascript
    const paragraphs = document.querySelectorAll("p");
    // paragraphs[0] is the first <p> element
    // paragraphs[1] is the second <p> element, etc.
    alert(paragraphs[0].nodeName);
    ```
27. What is HTML5 web Storage ? Explain localStorage and sessionStorage.
    - web storage: With web storage, web applications can store data locally within the user's browser.
    - Web storage is more secure, and large amounts of data can be stored locally, without affecting website performance.
    - the storage limit is far larger (at least 5MB) and information is never transferred to the server.
    - Web storage is per origin (per domain and protocol). All pages, from one origin, can store and access the same data.
    - window.localStorage - stores data with no expiration date
    - window.sessionStorage - stores data for one session (data is lost when the browser tab is closed)
28. What are data- attributes good for ?

    - allow us to store extra information on standard, semantic HTML elements without other hacks such as non-standard attributes, or extra properties on DOM.
    - Any attribute on any element whose attribute name starts with data- is a data attribute.

    ```html
    <article
      id="electric-cars"
      data-columns="3"
      data-index-number="12314"
      data-parent="cars"
    >
      ...
    </article>
    ```

    - using javascript can be get value from specified tag, here's the example:

    ```js
    const article = document.querySelector("#electric-cars");
    // The following would also work:
    // const article = document.getElementById("electric-cars")

    article.dataset.columns; // "3"
    article.dataset.indexNumber; // "12314"
    article.dataset.parent; // "cars"
    ```

    - not only javascript, it could be using as CSS access,

    ```css
    article::before {
      content: attr(data-parent);
    }
    article[data-columns="3"] {
      width: 400px;
    }
    article[data-columns="4"] {
      width: 600px;
    }
    ```

29. Explain the difference between cookies, session and local storage
    - Local storage has storing at client side(specified at browser), no expiration date, storage limit is about 10MB and data is never transferred to the server.
    - Cookies is client-side files or in browsers, limited capacity of 4 KB, not secured, no expiration date.
    - session is server-side files, limited capacity of up-to 128 MB, secure by server side and has expiration date when user logout or close the browser.
30. What are some differences that XHTML has compared to HTML ?
    - HTML has below atrributes:
      1. stands for Hypertext Markup Language.
      2. SGML application which is Standard Generalized Markup Language.
      3. not case sensitive.
      4. has similar document format.
      5. open tags accepted, etc: `<br>`.
      6. less expressive than XHTML.
      7. not mandatory for single root element.
      8. all content can be included in the body element.
      9. attribute values are not significant in HTML.
      10. no hard rules on the structure of the elements.
      11. requires a lenient HTML-specific paraser.
    - XHTML has below attributes:
      1. XHTML stands for Extensible Hypertext Markup Language.
      2. XML application stand for extensible markup language.
      3. case sensitive.
      4. uses markup language.
      5. all unclosed tags must be closed in XHTML.
      6. more expressive as compared to HTML.
      7. must contain at least one root element.
      8. all content must be put in blocks.
      9. attribute values are important in XHTML.
      10. the structure of the elements should be followed.
      11. XHTML needs to parse with a standard XML parser.
31. What are Web Workers ?

    - A web worker is a JavaScript that runs in the background, independently of other scripts, without affecting the performance of the page. You can continue to do whatever you want: clicking, selecting things, etc., while the web worker runs in the background.

    ```js
    // example
    <script>
    var w;

    function startWorker() {
      if (typeof(Worker) !== "undefined") {
        if (typeof(w) == "undefined") {
          w = new Worker("demo_workers.js");
        }
        w.onmessage = function(event) {
          document.getElementById("result").innerHTML = event.data;
        };
      } else {
        document.getElementById("result").innerHTML = "Sorry! No Web Worker support.";
      }
    }

    function stopWorker() {
      w.terminate();
      w = undefined;
    }
    </script>
    ```

32. What is the purpose of cache busting and how can you achieve it?
    - Cache busting solves the browser caching issue by using a unique file version identifier to tell the browser that a new version of the file is available. Therefore the browser doesn't retrieve the old file from cache but rather makes a request to the origin server for the new file.
    - In order to achieve cache-busting, can be use filename versioning and query strings versiong to do it.
    ```css
    /*
      filename
      style2.css or styles/v2/style.css
    */
    body {
      background-image: url(‘back-2.png’);
      background-color: #cccccc;
    }
    /*
      query strings
      style.css?back=2
    */
    body {
      background-image: url(‘back-new.png’);
      background-color: #cccccc;
    }
    ```
33. Discuss the differences between an HTML specification and a browser's implementation thereof.
    - HTML specifications such as HTML5 define a set of rules that a document must adhere to in order to be “valid” according to that specification.
    - In addition, a specification provides instructions on how a browser must interpret and render such a document.A browser is said to “support” a specification if it handles valid documents according to the rules of the specification.
    - As of yet, no browser supports all aspects of the HTML5 specification (although all of the major browser support most of it), and as a result, it is necessary for the developer to confirm whether the aspect they are making use of will be supported by all of the browsers on which they hope to display their content. This is why cross-browser support continues to be a headache for developers, despite the improved specificiations.
34. Describe the difference between a "cookie", "sessionStorage" and "localStorage".
    - It could be divide by two parts, the differences between cookies and storage first, and then find out the difference between localStorage and SessionStorage.
    - Differences between cookies and storage that cookies have limited size of capacity, it have only 4KB and storage can be 5 MB per domain. Also cookies are less secure than storage, might expire from time to time but storage will not expire unless user clears the cache in the browser.
    - Differences between localStorage and SessionStorage is expiration time, localStorage will not expire until user clear cache and sessionStorage will expire when user close the tab.
35. What does a DOCTYPE do ?
    - DOCTYPEs are required for legacy reasons. When omitted, browsers tend to use a different rendering mode that is incompatible with some specifications. Including the DOCTYPE in a document ensures that the browser makes a best-effort attempt at following the relevant specifications.
36. What is progressive rendering ?
    - Progressive Rendering is a technique in which once you render the critical content on the server, you start streaming it to the client without waiting for non-critical content
    - The browser starts to progressively render (paint) the HTML on the page as soon as a chunk for critical content is received. Non-critical content is then later rendered (paint) on the page when the browser receives it from the server.
37. Why you would use a srcset attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
    - You would use the srcset attribute when you want to serve different images to users depending on their device display width - serve higher quality images to devices with retina display enhances the user experience while serving lower resolution images to low-end devices increase performance and decrease data wastage (because serving a larger image will not have any visible difference).
    - For example:
      ```html
      <img
        srcset="small.jpg 500w, medium.jpg 1000w, large.jpg 2000w"
        src="..."
        alt=""
      />
      ```
      tells the browser to display the small, medium or large .jpg graphic depending on the client's resolution. Browser will serve specified img when user's closest resolution is.
    - `srcsets` solve the problem whereby you want to serve smaller image files to narrow screen devices, as they don't need huge images like desktop displays do — and also optionally that you want to serve different resolution images to high density/low-density screens.
38. What is the purpose of "main" element ?
    - The `<main>` HTML element represents the dominant content of the `<body>` of a document.
    - The main content area consists of content that is directly related to or expands upon the central topic of a document, or the central functionality of an application.
    - The content of a `<main>` element should be unique to the document. Content that is repeated across a set of documents or document sections such as sidebars, navigation links, copyright information, site logos, and search forms shouldn't be included unless the search form is the main function of the page.
39. What is an HTML preprocessor and are you using it ?
    - Pre-processor is a program that accepts one form of data input & converts it to another form of input data, usually in HTML & CSS. The pre-processor is made for the purpose of including new features with the existing ones without violating the browser compatibility.
    - HAML Pre-processor: Haml stands for HTML Abstraction Markup Language, created by Hampton Catlin and the only objective behind creating it is to make the markup beautiful.
    ```html
    %body %center %header %h1GeeksforGeeks %section %bA Computer Science Portal
    for Geeks
    ```
40. What are the building blocks of HTML5 ?
    - An HTML document consist of its basic building blocks which are:
      1. Tags: An HTML tag surrounds the content and apply meaning to it. It is written between < and > brackets.
      2. Attribute: An attribute in HTML provides extra information about the element, and it is applied within the start tag. An HTML attribute contains two fields: name & value.
41. Why to use HTML5 semantic tags ?
    - HTML5’s semantic elements help structure the code we create, making it more readable and easier to maintain.
    - help us think about the structure of our dynamic data, and to choose the titles’ hierarchy properly
    - help us differentiate the semantic elements of our markup from the ones we use solely for layout
    - HTML5 semantic elements push us to learn the meanings of HTML elements and better understand our audiences, particularly those who live with disabilities.
42. How would you select svg or canvas for your site ?
    - When you need to high quality resolution, flexibility and responsiveness of the graphic, smaller file size than JPG, also the JS, CSS accessibility. svg is the way.
    - When you need impressive 3D or immersive stuff, movement of difference object and control the pixels, also using the canvas API. canvas is the way.
43. What kind of things must you be wary of when designing or developing for multilingual sites ?
    - Use lang attribute in your HTML.
    - Directing users to their native language - Allow a user to change his country/language easily without hassle.
    - Text in raster-based images (e.g. png, gif, jpg, etc.), is not a scalable approach - Placing text in an image is still a popular way to get good-looking, non-system fonts to display on any computer. However, to translate image text, each string of text will need to have a separate image created for each language. Anything more than a handful of replacements like this can quickly get out of control.
    - Restrictive words/sentence length - Some content can be longer when written in another language. Be wary of layout or overflow issues in the design. It's best to avoid designing where the amount of text would make or break a design. Character counts come into play with things like headlines, labels, and buttons. They are less of an issue with free-flowing text such as body text or comments.
    - Be mindful of how colors are perceived - Colors are perceived differently across languages and cultures. The design should use color appropriately.
    - Formatting dates and currencies - Calendar dates are sometimes presented in different ways. Eg. "May 31, 2012" in the U.S. vs. "31 May 2012" in parts of Europe.
    - Do not concatenate translated strings - Do not do anything like "The date today is " + date. It will break in languages with different word order. Use a template string with parameters substitution for each language instead. For example, look at the following two sentences in English and Chinese respectively: I will travel on {% date %} and {% date %} 我会出发. Note that the position of the variable is different due to grammar rules of the language.
    - Language reading direction - In English, we read from left-to-right, top-to-bottom, in traditional Japanese, text is read up-to-down, right-to-left.
    - Useful-to-have - include the locale in the path (e.g en_US, zh_CN, etc).
44. What is WebP ?
    - WebP is a modern image format that provides superior lossless and lossy compression for images on the web. Using WebP, webmasters and web developers can create smaller, richer images that make the web faster.
    - WebP lossless images are 26% smaller in size compared to PNGs. WebP lossy images are 25-34% smaller than comparable JPEG images at equivalent SSIM quality index.
    - Lossless WebP supports transparency (also known as alpha channel) at a cost of just 22% additional bytes. For cases when lossy RGB compression is acceptable, lossy WebP also supports transparency, typically providing 3× smaller file sizes compared to PNG.
45. Why do I need a doctype and what does it do ?
    - All browsers need the doctyp. Without the DOCTYPE you are forcing the browsers to render in Quirks Mode.
    - The DOCTYPE declaration is `<!DOCTYPE html>` and is case-insensitive in the HTML syntax. DOCTYPEs from earlier versions of HTML were longer because the HTML language was SGML-based and therefore required a reference to a DTD. With HTML5 this is no longer the case and the DOCTYPE is only needed to enable standards mode for documents written using the HTML syntax. Browsers already do this for `<!DOCTYPE html>`.
46. What's the difference between Full Standard, Almost Standard and Quirks Mode ?
    - Quirks modes: Layout emulates non-standard behavior as supported by old browsers.
    - Almost standard modes: A small number of quirks/old behavior are supported while rendering the layout.
    - Full standard modes: Layout emulates standard behavior as described by HTML and CSS specifications.
47. Could you generate a public key in HTML ?
    - You can easily generate a public key using the <keygen> tag in HTML. The <keygen> element generates an encryption key for passing encrypted data to a server. The purpose of the <keygen> element is to provide a secure way to authenticate users.
    - Actually, when a form is submitted then two keys are generated, private key and public key. The private key is stored locally, and the public key is sent to the server. The public key is used to generate a client certificate to authenticate the user for the future.
    ```html
    <keygen
      name="name"
      challenge="challenge"
      keytype="type"
      keyparams="pqg-params"
    ></keygen>
    ```
48. Why is it generally a good idea to position CSS `<link>` between `<head>` `</head>` and JS `<script>` just before `<body>`? Do you know any exceptions ?
    - The css files are placed in the "head" so that they load and the page is seen as it should be.
    - The Javascript files are placed before closing the "body", so that they enhance their function once the entire page is loaded.
49. What are Web Components ?
    - Web Components aims to solve such problems — it consists of three main technologies, which can be used together to create versatile custom elements with encapsulated functionality that can be reused wherever you like without fear of code collisions.
    1. Custom elements: A set of JavaScript APIs that allow you to define custom elements and their behavior, which can then be used as desired in your user interface.
    2. Shadow DOM: A set of JavaScript APIs for attaching an encapsulated "shadow" DOM tree to an element — which is rendered separately from the main document DOM — and controlling associated functionality. In this way, you can keep an element's features private, so they can be scripted and styled without the fear of collision with other parts of the document.
    3. HTML templates: The `<template>` and `<slot>` elements enable you to write markup templates that are not displayed in the rendered page. These can then be reused multiple times as the basis of a custom element's structure.
50. What is an IndexedDB ?

    - ndexedDB is a transactional database system, like an SQL-based RDBMS. However, unlike SQL-based RDBMSes, which use fixed-column tables, IndexedDB is a JavaScript-based object-oriented database. IndexedDB lets you store and retrieve objects that are indexed with a key; any objects supported by the structured clone algorithm can be stored.
    - You need to specify the database schema, open a connection to your database, and then retrieve and update data within a series of transactions.

    ```js
    let db;
    const request = indexedDB.open("MyTestDatabase");
    request.onerror = (event) => {
      console.log("Why didn't you allow my web app to use IndexedDB?!");
    };
    request.onsuccess = (event) => {
      db = event.target.result;
    };

    request.onupgradeneeded = (event) => {
      // Save the IDBDatabase interface
      const db = event.target.result;

      // Create an objectStore for this database
      const objectStore = db.createObjectStore("name", { keyPath: "myKey" });
    };
    ```

51. What is accessibility & ARIA role means in a web application?
    - Accessible Rich Internet Applications (ARIA) is a set of roles and attributes that define ways to make web content and web applications (especially those developed with JavaScript) more accessible to people with disabilities.
    - It supplements HTML so that interactions and widgets commonly used in applications can be passed to assistive technologies when there is not otherwise a mechanism. For example, ARIA enables accessible JavaScript widgets, form hints and error messages, live content updates, and more.
    ```html
    <div
      id="percent-loaded"
      role="progressbar"
      aria-valuenow="75"
      aria-valuemin="0"
      aria-valuemax="100"
    ></div>
    ```
