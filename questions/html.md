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
    <meta name="description" content="I am a web page with description"> 
    <title>Home Page</title>
    </head>
    <body>
    
    </body>
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
    <META NAME="keywords" CONTENT="keyword keyword keyword keyword">
    <META NAME="description" CONTENT="description of your site">
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
    <meta http-equiv="Content-Type" content="text/html;charset=ISO-8859-1">
    // html5
    <meta charset="UTF-8">
    ```
10. What is a self closing tag ?
    - In HTML5 it is not strictly necessary to close certain HTML tags. The tags that aren't required to have specific closing tags are called "self closing" tags.
    - An example of self closing tag is something like a line break (<br />) or the meta tag (<meta>). This means that the following are both acceptable:
    ```html
    <meta charset="UTF">
    ```