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
8. Briefly describe the correct usage of the following HTML5 semantic elements: <header>, <article>, <section>, <footer>
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
    - The <small> HTML element represents side-comments and small print, like copyright and legal text, independent of its styled presentation. In general, it renders text within it one font-size smaller, such as from small to x-small.
13. Explain the difference between block elements and inline elements.
    - Block elements: They consume the entire width available irrespective of their sufficiency. They always start in a new line and have top and bottom margins. It does not contain any other elements next to it.
      etc: <h1>-<h6>,<div>,<hr>,<li>,<ul>,<ol>,<p>,<table>,<header>,<nav>,<footer>,<main>,<section>,<article>,<aside>
    - Inline elements: They occupy only enough width that is sufficient to it and allows other elements next to it which are inline. Inline elements don't start from a new line and don't have top and bottom margins as block elements have.
      etc:<a>,<br>,<script>,<input>,<img>,<span>,<b>,<label>
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
    - header and footer: there is no longer a need to identify the two elements with a <div> tag. Footer is placed at the end of the web page while header is placed at the start of the web page. With this tag, browser will know load which one first.
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
    -
