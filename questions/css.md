1. Explain the three main ways to apply CSS styles to a web page
- Using the inline style attribute on an element
```html
<div>
    <p style="color: maroon;"></p>
</div>
```
- Using a `<style>` block in the `<head>` section of your HTML
```html
<head>
    <title>CSS Refresher</title>
    <style>
        body {
            font-family: sans-serif;
            font-size: 1.2em;
        }
    </style>
</head>
```
- Loading an external CSS file using the `<link>` tag
```html
<head>
    <title>CSS Refresher</title>
    <link rel="stylesheet" href="/css/styles.css" />
</head>
```
2. What is CSS ?
- CSS stands for Cascading Style Sheets. CSS is used to define styles for your web pages, including the design, layout and variations in display for different devices and screen sizes.
CSS was intended to allow web professionals to separate the content and structure of a website's code from the visual design.

3. How to use variables in Sass?
- Think of variables as a way to store information that you want to reuse throughout your stylesheet. You can store things like colors, font stacks, or any CSS value you think you'll want to reuse. Sass uses the $ symbol to make something a variable.
```scss
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```
4. Explain CSS sprites, and how you would implement them on a page or site  
- CSS sprites combine multiple images into one single larger image. It is commonly used technique for icons (Gmail uses it).
    1. Use a sprite generator that packs multiple images into one and generate the appropriate CSS for it.
    2. Each image would have a corresponding CSS class with `background-image`, `background-position` and `background-size` properties defined.
    3. To use that image, add the corresponding class to your element.
- Advantages:
    1. Reduce the number of HTTP requests for multiple images (only one single request is required per spritesheet). But with HTTP2, loading multiple images is no longer much of an issue.
    2. Advance downloading of assets that won’t be downloaded until needed, such as images that only appear upon `:hover` pseudo-states. Blinking wouldn't be seen.

5. Explain the CSS `box model` and the layout components that it consists of 
- The CSS box model is a rectangular layout paradigm for HTML elements that consists of the following:
    1. Content - The content of the box, where text and images appear
    2. Padding - A transparent area surrounding the content (i.e., the amount of space between the border and the content)
    3. Border - A border surrounding the padding (if any) and content
    4. Margin - A transparent area surrounding the border (i.e., the amount of space between the border and any neighboring elements)
6. What is a CSS rule ?
- Web browsers apply CSS rules to a document to affect how they are displayed. A CSS rule is formed from:
    1. A set of properties, which have values set to update how the HTML content is displayed,
    2. A selector, which selects the element(s) you want to apply the updated property values to.
- A set of CSS rules contained within a stylesheet determines how a webpage should look.
7. Explain what is a `@extend` directive used for in Sass? 
- Using `@extend` lets you share a set of CSS properties from one selector to another. It helps keep your Sass very dry.
Consider:
```css
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}

.warning {
  @extend %message-shared;
  border-color: yellow;
}
```
CSS output:
```css
.message, .success, .error, .warning {
  border: 1px solid #cccccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```
8. Have you played around with the new CSS `Flexbox` or `Grid` specs?  
- Yes. Flexbox is mainly meant for 1-dimensional layouts while Grid is meant for 2-dimensional layouts.
- Flexbox solves many common problems in CSS, such as vertical centering of elements within a container, sticky footer, etc. Bootstrap and Bulma are based on Flexbox, and it is probably the recommended way to create layouts these days. Have tried Flexbox before but ran into some browser incompatibility issues (Safari) in using flex-grow, and I had to rewrite my code using inline-blocks and math to calculate the widths in percentages, it wasn't a nice experience.
- Grid is by far the most intuitive approach for creating grid-based layouts (it better be!) but browser support is not wide at the moment.
9.  What is DOM (Document Object Model) and how is it linked to CSS?  
- The Document Object Model (DOM) is a cross-platform and language-independent application programming interface that treats an HTML, XHTML, or XML document as a tree structure wherein each node is an object representing a part of the document.
- With the Document Object Model, programmers can create and build documents, navigate their structure, and add, modify, or delete elements and content. The DOM specifies interfaces which may be used to manage XML or HTML documents.
- When a browser displays a document, it must combine the document's content with its style information. The browser converts HTML and CSS into the DOM (Document Object Model). The DOM represents the document in the computer's memory. It combines the document's content with its style.
10. What is Sass ?
- `Sass` or `Syntactically Awesome StyleSheets` is a CSS preprocessor that adds power and elegance to the basic language. It allows you to use variables, nested rules, mixins, inline imports, and more, all with a fully CSS-compatible syntax. Sass helps keep large stylesheets well-organized, and get small stylesheets up and running quickly.
- A CSS preprocessor is a scripting language that extends CSS by allowing developers to write code in one language and then compile it into CSS.
11. What existing CSS frameworks have you used locally, or in production? How would you change/improve them? 
- `Bootstrap` - Slow release cycle. Bootstrap 4 has been in alpha for almost 2 years. Add a spinner button component, as it is widely used.
- `Semantic UI` - Source code structure makes theme customization extremely hard to understand. Its unconventional theming system is a pain to customize. Hardcoded config path within the vendor library. Not well-designed for overriding variables unlike in Bootstrap.
- `Bulma` - A lot of non-semantic and superfluous classes and markup required. Not backward compatible. Upgrading versions breaks the app in subtle manners.
12. Describe `floats` and how they work 
- Float is a CSS positioning property. Floated elements remain a part of the flow of the web page. This is distinctly different than page elements that use absolute positioning. Absolutely positioned page elements are removed from the flow of the webpage.
```css
#sidebar {
  float: right; // left right none inherit			
}
```
- The CSS clear property can be used to be positioned below `left/right/both` floated elements.
13. What Selector Nesting in Sass is used for? 
- Sass let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML. CSS, on the other hand, doesn't have any visual hierarchy.
Consider example (scss):
```scss
.parent {
  color: red;

  .child {
    color: blue;
  }
}
```
Result (css):
```scss
.parent {
  color: red;
}

.parent .child {
  color: blue;
}
```
14. List out the key features for Sass 
- Key features for Sass include
    1. Full CSS3-compatible
    2. Language extensions such as nesting, variables, and mixins
    3. Many useful functions for manipulating colors and other values
    4. Advanced features like control directives for libraries
    5. Well-formatted, customizable output
15. What is the difference between `classes` and `IDs` in CSS?
- `IDs` — Meant to be unique within the document. Can be used to identify an element when linking using a fragment identifier. Elements can only have one id attribute.
- `Classes` — Can be reused on multiple elements within the document. Mainly for styling and targeting elements.
16.  List out the data types that Sass supports  
- Sass supports seven main data types:
    1. `Numbers` - most of the time they are accompanied by a unit of some sort but they are still technically numbers. You can perform basic mathematical operations on these values.
    ```scss
    $size: 18;                  // A number
    $px-unit: $size * 1px;      // A pixel measurement
    $px-string: $size + px;     // A string
    $px-number: $px-unit / 1px; // A number
    ```
    2. `Strings` - just like CSS, accepts both quoted and unquoted strings, even if they contain spaces
    ```scss
    $website: 'SitePoint'; // Stores SitePoint
    $name: 'Gajendar' + ' Singh';  // 'Gajendar Singh'
    $date:  'Month/Year : ' + 3/2016; // 'Month/Year : 3/2016'
    $date:  'Month/Year : ' + (3/2016); // 'Month/Year : 0.00149' 
    // This is because 3/2016 is evaluated first.
    $variable: 3/2016;      // Evaluated to 0.00149
    ```
    3. Colors - CSS color expressions come under the `color` data type. You can refer to the colors in hexadecimal notation, as `rgb, rgba, hsl and hsla` values or use native keywords like `pink, blue`, etc.
    ```scss
    $color: yellowgreen;           // #9ACD32
    color: lighten($color, 15%);    // #b8dc70
    color: darken($color, 15%);     // #6c9023
    color: saturate($color, 15%);   // #a1e01f
    color: desaturate($color, 15%); // #93ba45
    color: (green + red);           // #ff8000
    ```
    4. Booleans - has only two possible values: true and false
    ```scss
    $i-am-true: true;

    body {
    @if not $i-am-true {
        background: rgba(255, 0, 0, 0.6);
    } @else {
        background: rgba(0, 0, 255, 0.6); // expected
    }
    }
    ```
    5. Null - is commonly used to define an empty state, neither true or false. This is typically the value you want to set when defining a variable without a value, only to prevent the parser from crashing.
    ```scss
    .foo {
    content: type-of(null); // null
    content: type-of(NULL); // string
    $bar: 'foo' + null; // invalid null operation: "foo plus null”.
    }
    ```
    6. Lists - are just the Sass version of arrays. You can store multiple types of values in a list.
    ```scss
    $font-list: 'Raleway','Dosis','Lato'; // Three comma separated elements
    $pad-list: 10px 8px 12px; // Three space separated elements
    $multi-list: 'Roboto',15px 1.3em; // This multi-list has two lists.
    ```
    7. Maps - Sass maps are like associative arrays. A map stores both keys and values associated with those keys.
    ```scss
    $styling: (
    'font-family': 'Lato',
    'font-size': 1.5em,
    'color': tomato,
    'background': black
    );

    h1 {
    color: map-get($styling, 'color');
    background: map-get($styling, 'background');
    }
    ```
17. What's the difference between SCSS and Sass ?
- SASS (Syntactically Awesome Style Sheets) is a pre-processor scripting language that will be compiled or interpreted into CSS. SassScript is itself a scripting language whereas SCSS is the main syntax for the SASS which builds on top of the existing CSS syntax. It makes use of semicolons and brackets like CSS (Cascaded Style Sheets).
- SASS and SCSS can import each other. Sass actually makes CSS more powerful with math and variable support. 
- Let’s list down the main difference between SASS and SCSS. 
    1. SASS is used when we need an original syntax, code syntax is not required for SCSS.
    2. SASS follows strict indentation, SCSS has no strict indentation.
    3. SASS has a loose syntax with white space and no semicolons, the SCSS resembles more to CSS style and use of semicolons and braces are mandatory.
    4. SASS file extension is .sass and SCSS file extension is .scss.
    5. SASS has more developer community and support than SCSS.
    6. SASS supports SassDoc to add documentation whereas SCSS allows inline documentation.
    7. SASS can’t be used as CSS and vice-versa whereas a valid CSS code is also a valid SCSS code.
    8. SASS is hard to add to existing CSS projects whereas SCSS can be added easily to an existing CSS project just by adding new code.
18. Explain the usage of `table-layout` property
- The table-layout property defines the algorithm used to lay out table cells, rows, and columns.
- Tip: The main benefit of table-layout: fixed; is that the table renders much faster. On large tables, users will not see any part of the table until the browser has rendered the whole table. So, if you use table-layout: fixed, users will see the top of the table while the browser loads and renders rest of the table. This gives the impression that the page loads a lot quicker!
```css
table.a {
  table-layout: auto;
  width: 180px;
}

table.b {
  table-layout: fixed;
  width: 180px;
}
```
19. What's the difference between a `relative`, `fixed`, `absolute` and `static` ally positioned element ?
- An important concept to understand first is that every single element on a web page is a block. Literally a rectangle of pixels. This is easy to understand when you set the element to display: block; or if that element is block-level by default like a `<div>`. This means you can set a width and a height and that element will respect that. But elements that are display: inline;, like a `<span>` by default, are also rectangles, they just flow onto the page differently, lining up horizontally as they can.
```css
.el {
  position: static;
  position: relative;
  position: absolute;
  position: fixed;
  position: sticky;
  position: inherit;
}
```
- `static`: This is the `default` for every single page element. Different elements don’t have different default values for positioning, they all start out as static. Static doesn’t mean much; it just means that the element will flow into the page as it normally would. The only reason you would ever set an element to position: static; is to forcefully remove some positioning that got applied to an element outside of your control. This is fairly rare, as positioning doesn’t cascade.
- `relative`: 
    1. This type of positioning is probably the most confusing and misused. What it really means is “relative to itself”. If you set position: relative; on an element but no other positioning attributes (top, left, bottom or right), it will have no effect on it’s positioning at all, it will be exactly as it would be if you left it as position: static; But if you do give it some other positioning attribute, say, top: 10px;, it will shift its position 10 pixels down from where it would normally be. I’m sure you can imagine, the ability to shift an element around based on its regular position is pretty useful. I find myself using this to line up form elements many times that have a tendency to not want to line up how I want them to.
    2. There are two other things that happen when you set position: relative; on an element that you should be aware of. One is that it introduces the ability to use z-index on that element, which doesn’t work with statically positioned elements. Even if you don’t set a z-index value, this element will now appear on top of any other statically positioned element. You can’t fight it by setting a higher z-index value on a statically positioned element.
    3. The other thing that happens is it limits the scope of absolutely positioned child elements. Any element that is a child of the relatively positioned element can be absolutely positioned within that block
- `absolute`:
    1. This is a very powerful type of positioning that allows you to literally place any page element exactly where you want it. You use the positioning attributes top, left, bottom, and right to set the location. Remember that these values will be relative to the next parent element with relative (or absolute) positioning. If there is no such parent, it will default all the way back up to the `<html>` element itself meaning it will be placed relative to the page itself.
    2. The trade-off (and most important thing to remember) about absolute positioning is that these elements are removed from the flow of elements on the page. An element with this type of positioning is not affected by other elements and it doesn’t affect other elements. This is a serious thing to consider every time you use absolute positioning. Its overuse or improper use can limit the flexibility of your site.
- `fixed`:
    1. A fixed position element is positioned relative to the viewport, or the browser window itself. The viewport doesn’t change when the window is scrolled, so a fixed positioned element will stay right where it is when the page is scrolled.
    2. This might be used for something like a navigation bar that you want to remain visible at all times regardless of the pages scroll position. The concern with fixed positioning is that it can cause situations where the fixed element overlaps content such that is is inaccessible
- `sticky`:Sticky positioning is really unique! A sticky element will just sit there like a static element, but as you scroll past it, if it’s parent element has room (usually: extra height) the sticky element will behave as if it’s fixed until that parent element is out of room.
20. Have you ever worked with retina graphics ? If so, when and what techniques did you use ?
- Retina graphics lay emphasis on the double density pixels screen of its devices. There are different CSS techniques you can use… like CSS pixel. It is an abstract unit used by the browsers to draw images and other content on a web page. CSS pixels are DIPs which means they are device independent pixels. They readjust themselves according to the pixel density of the screen they are rendered in. You can also resize images in media queries for higher resolution.
21. What are the advantages/disadvantages of using CSS preprocessors ?
- Advantages:
    1. Nested syntax
    2. Ability to define variables
    3. Ability to define mixins
    4. Mathematical functions
    5. Operational functions (such as “lighten” and “darken”)
    6. Joining of multiple files
- Disadvantages:
    1. Dubugging is harder
    2. Compilation time slows down development
22. How is responsive design different from adaptive design ?
- Responsive Design adjusts its content and width according to the device; Adaptive design loads the content of the web page that was already designed;
- Designer have to work less because they have to create the single layout of the page designers in responsive design; Designers have to work more because they have to create six different versions of the site to handle different screen sizes for Adaptive design.
- Responsive design easy to adapt new layout even screen come to market and the content will adjust accordingly; Adaptive design needs designer to develop entire new page if the new screen come to market
- Responsive Design works well for larger sites that are being built from the scratch; Adaptive Design works well for smaller sites that are being refreshed.
- Responsive design is smooth because the layout adjusts in the flow regardless of the device being viewed; Adaptive design snaps into place since the website is serving something different which relies on device or browser used to view it.
- Use of Responsive Design: It has been made easier for less experienced designers and developers to use Responsive Design with the availability of themes via CMS systems such as WordPress, Joomla, and many more; Use of Adaptive Design: Adaptive is handy for updating an existing site to make it more mobile-friendly.
23. What is CSS selectors ? Name some.
- CSS element selector: the element selector selects HTML elements based on the element name:
```css
p {
  text-align: center;
  color: red;
}
```
- CSS element id selector: the CSS id selector selects id attribute of an HTML element to select a specific element.
```css
#para1 {
  text-align: center;
  color: red;
}
```
- CSS class selector: To select elements with a specific class, write a period (.) character, followed by the class name.
```css
.center {
  text-align: center;
  color: red;
}
```
- CSS universal selector: The universal selector (*) selects all HTML elements on the page.
```css
* {
    text-align: center;
    color: blue;
}
```
- CSS grouping selector: The grouping selector selects all the HTML elements with the same style definitions.
```css
h1 {
  text-align: center;
  color: red;
}

h2 {
  text-align: center;
  color: red;
}

p {
  text-align: center;
  color: red;
}
```
24. What does Accessibility (a11y) mean ?
- Accessibility refers to how software or hardware combinations are designed to make a system accessible to persons with disabilities, such as:
    1. Visual impairment
    2. Hearing loss
    3. Limited dexterity
- For example, a website developed with accessibility in mind might have text-to-speech capabilities or output for special braille hardware geared toward individuals with visual impairments. In today’s internet-driven world, the accessibility of a website is paramount in order for it to reach all audiences.
- Accessibility also can be incorporated with other forms of media, like pictures and videos. An example of accessibility built into media is subtitles. In this case, a film may not be produced for the hard of hearing, but subtitles help make the film more enjoyable for those with this impairment.
- The word accessibility is abbreviated to "a11y," with the number eleven in the middle referring to the number of letters that the word contains between the first and last letter. It follows an information and communications technology (ICT)-oriented convention, just like internationalization (i18n) and localization (l10n), which are used mostly in the software community.
25. What is CSS preprocessor and why to use one ?
- A CSS preprocessor is a scripting language that extends CSS and is compiled into regular CSS syntax. A browser can only understand CSS, which at times may not be enough to write clean and reusable rules. Using only CSS, the designer/developer is not able to reuse a collection of rules in multiple selectors which had unclear pieces of data across a stylesheet. To overcome most of these limitations, the concept of a preprocessor was created. It offered an advanced way of writing CSS that extends the basic functionalities. This advanced code is later compiled as normal CSS code that the browser will understand.
- The preprocessor will make your code easier to maintain, make your CSS DRY, originize the CSS structure, and save the dev time.
26. How would you approach fixing browser-specific styling issues ?
- Always build responsive layouts
- Check features of HTML5 and CSS3 on caniuse.com to see what browser support there is for something new I want to use and avoid things that have sketchy support at this time.
- Develop all of the views at the same time and test across browsers and operating systems as I go to avoid getting something that looks nice in my favorite browser, but breaks in other places that I then have to fix later with the potential of having to start from scratch.
- Realize that we don’t have to make the display on every browser exactly identical as long as what we make looks good in each browser. Graceful degradation means that your design is able to fall back to a decent, but simplified, version of the layout rather than just looking broken in browsers that don’t support certain features of HTML or CSS.
- Keep up-to-date on what browsers and systems my target-audience is using, either by looking at Google Analytics on the existing site I’m replacing for the client, or periodically checking Stat Counter.
- Use BrowserStack for more intense cross-browser testing.
- Use the knowledge and experience I’ve gained from my years in web development to know in advance what to avoid or what to do to make something work in all the browsers.
27. What's the difference between resetting and normalizing CSS ? Which would you choose, and why ?
- Normalize.css preserves useful defaults rather than "unstyling" everything. For example, elements like `sup` or `sub` "just work" after including normalize.css (and are actually made more robust) whereas they are visually indistinguishable from normal text after including reset.css. So, normalize.css does not impose a visual starting point (homogeny) upon you. This may not be to everyone's taste. The best thing to do is experiment with both and see which gels with your preferences
- Normalize.css corrects some common bugs that are out of scope for reset.css. It has a wider scope than reset.css, and also provides bug fixes for common problems like: display settings for HTML5 elements, the lack of `font` inheritance by form elements, correcting `font-size` rendering for `pre`, SVG overflow in IE9, and the `button` styling bug in iOS.
- Normalize.css doesn't clutter your dev tools. A common irritation when using reset.css is the large inheritance chain that is displayed in browser CSS debugging tools. This is not such an issue with normalize.css because of the targeted stylings.
- Normalize.css is more modular. The project is broken down into relatively independent sections, making it easy for you to potentially remove sections (like the form normalizations) if you know they will never be needed by your website.
- Normalize.css has better documentation. The normalize.css code is documented inline as well as more comprehensively in the GitHub Wiki. This means you can find out what each line of code is doing, why it was included, what the differences are between browsers, and more easily run your own tests. The project aims to help educate people on how browsers render elements by default, and make it easier for them to be involved in submitting improvements.
28. Explain your understanding of the `box` model and how you would tell the browser in CSS to render your layout in different box models.
- The box model is really just a series of directives that define how the various layout specifications of an element interact with one another. The components covered by the box model are:
    1. document canvas
    2. marigins
    3. borders
    4. padding
    5. element widths and heights
    6. child element properties
- The basic rule is that the computed width or height of an element is equal to:
    1. margin + border + padding + (width|height)
- In many cases the width and/or height will be set to its default value of auto, meaning that the canvas area put aside for content is equal to:
    1. available_canvas − margin − padding − border
- In such an equation, available_canvas is itself a discrete (if often auto-computed) value, less the amount of margins, borders and padding. This number is most important for the width of elements, because width calculation errors on the part of a designer will have the undesirable result of causing a horizontal scroll bar to appear in the browser window. Additionally, browsers always place elements at the left margin of the browser canvas that would otherwise overflow beyond the right margin of the browser window, unless instructed to do otherwise.
29. Desribe `pseudo-elements` and discuss what they are used for.
- A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s). For example, `::first-line` can be used to change the font of the first line of a paragraph.
```css
p::first-line {
  color: blue;
  text-transform: uppercase;
}
```
- Style the first letter, or line, of an element
Insert content before, or after, the content of an element
30. How does CSS actually work (under the hood of browser) ?
- Working: 
    1. The browser loads the HTML and is converted into DOM (Document Object Model).
    2. Most of the resources are then fetched that is linked to the HTML document such as embedded videos, images, and linked CSS.
    3. The CSS fetched is then parsed by the browser. Based on the selector type used, it figures out which style is to be applied on which nodes in the DOM and attaches styles to them. These are called render trees.
    4. After the rules have been applied to the render tree, its layout structure should appear.
    5. At the Painting stage, a visual display of the page is shown on the screen.
31. What is a Grid System in CSS ?
- A grid can be defined as an intersecting set of vertical and horizontal lines. CSS Grid layout separates a page into major sections. Grid property offers a grid-based layout system having rows and columns. It makes the designing of web pages easy without positioning and floating. The grid layout gives us a way to create grid structures depicted in CSS, not in HTML.

- Similar to the table, it enables a user to align the elements into rows and columns. But compare to tables, it is easy to design layout with the CSS grid. We can define columns and rows on the grid by using grid-template-rows and grid-template-columns properties.

- A grid container can be created by declaring the display: grid or display: inline-grid on an element. Grid container contains the items of a grid that are placed inside the rows and columns.
32. Explain the purpose of clearing floats in CSS.
- Purpose of clearing floats in CSS: We clear the float property to control the floating elements by preventing overlapping. On our webpage, if an element fits horizontally next to the floated elements, unless we apply the clear property same as float direction then the elements will be a move below the floated elements. 
```
clear: none|right|left|both|initial|inherit;
```
33. What does `* { box-sizing: border-box;}` do ? What are its advantages ?
- The default value for box-sizing is content-box. If you set box-sizing value to border-box the width of the box remains same even if you add padding, and the content inside the box shrink accordingly.
34. Can you explain the difference between coding a website to be responsive versus using a mobile-first startegy ?
- The main difference between responsive web design and mobile-first design is how the designer approaches the website. A responsive website is reactive — the design moving fluidly to fit devices. A mobile-first website is when the mobile website planned and designed in tandem with the desktop site, making proactive changes to the overall design to ensure the mobile experience is just as good as the desktop experience.
- While both designs make your school or district’s website accessible on all devices, a mobile-first experience offers a better overall user experience because a variety of considerations are taken into account during the design phase, such as white space, font size, and load time.
35. Explain the basic rules of CSS Specificity.
- Specificity Rules include:  
    1. CSS style applied by referencing external stylesheet has lowest precedence and is overridden by Internal and inline CSS.
    2. Internal CSS is overridden by inline CSS.
    3. Inline CSS has highest priority and overrides all other selectors.
36. How do you optimize your webpages for print ?
- Remove background colors and images:
    1. remove background colors and images then apply a white background instead.
- Adjust text for readability:
    1. Use high contrast between your background and text
    2. Adjust font sizing improve readability
    3. Evaluate your font choice and if it works well when printed
- Hide web-only functionality:
    1. This can be done using display: none; to hide the desired elements.
- Optimize imagery:
    1. For images that should remain on the page, consider the sizing and placement. For example, decrease the size of large images to avoid taking up too much real estate on the page.
- Overwrite unsupported styles:
    1. implementing fallbacks to avoid layout issues when your content is printed
- Control page breaking:
    1. use the page-break-before, page-break-after, and page-break-inside properties to control how content breaks between pages to further optimize readability.
- Prevent widows and orphans:
    1. Use the widows property to define the minimum number of lines that should break to the top of the next page. Setting it to a value higher than one will prevent printed pages with a single line of text at the top.
    2. The orphans property is similar, but instead of defining how many lines are on the next page, it set the minimum number of lines to display at the bottom of the page. Setting it to a value higher than one will prevent single lines from displaying at the bottom of a page.
- Add contextual content:
    1. Consider using CSS generated content with the :before and :after pseudo elements to add context to certain elements.
    ```css
    a[href]:after {
    content: " (" attr(href) ")";
    }
    ```
37. Have you ever used a grid system, and if so what do you prefer ?
- The float-based grid system was the most reliable because it still has the most browser support among the alternative existing systems (flex, grid). Bootstrap was using the float approach until Bootstrap 4 which switched to the flex-based approach. Flex is the recommended approach for building grid systems and has decent browser support. But I am almost confident that with the broader adoption of CSS Grid, it will turn into the main layout standard.
38. What are the different ways to visually hide content (and make it available only for screen readers) ?
- `display:none or visibility: hidden`:These styles will hide content from all users. The content is removed from the visual flow of the page and is ignored by screen readers. Do not use this CSS if you want the content to be read by a screen reader. But DO use it for content you want hidden from all users.
- `hidden attribute`:The HTML hidden attribute is relatively new and not supported on older browsers like IE11. When supported, it functions the same as CSS display:none—elements with this attribute will not be presented to any user.
- `width:0px, height:0px or other 0 pixel sizing techniques (not recommended)`:An element with no height or width, whether defined in HTML or CSS, is typically removed from the flow of the page, so most screen readers will not read it. Do not size content to 0 pixels if you want the content to be read by a screen reader. Content styled with font-size:0px or line-height:0 may work, though the elements would still take horizontal space on the screen. All these techniques may result in search engine penalties as they may be interpreted as malicious.
- `text-indent: -10000px`:This approach moves the content to the left 10000 pixels - thus off the visible screen. Screen readers will still read text with this style.
However, if a link, form control, or other focusable element is given this style, the element would be focusable, but not visible on the page—sighted keyboard users would likely be confused. This approach may be a viable option if the element does not contain navigable elements, though better techniques are available.
- `Absolutely positioning content off-screen`: 
    1. The following are the recommended styles for visually hiding content that will be read by a screen reader.
    ```css
    .sr-only {
    position:absolute;
    left:-10000px;
    top:auto;
    width:1px;
    height:1px;
    overflow:hidden;
    }
    ```
    2. The .sr-only CSS class ("sr-only" meaning "screen reader only", though the class name does not really matter) should then be referenced from within the tag of the element being hidden, as shown:
    ```html
    <div class="sr-only">This text is hidden.</div>
    ```
- `CSS clip`:
```css
{clip: rect(1px, 1px, 1px, 1px);
clip-path: inset(50%);
height: 1px;
width: 1px;
margin: -1px;
overflow: hidden;
padding: 0;
position: absolute;}
```
39. Describe `z-index` and how a stacking context is formed.
- The z-index:
    1. property specifies the stack order of an element.
    2. An element with greater stack order is always in front of an element with a lower stack order.
- The default stacking context is the root element, `<html>`. A stacking context is created when an element is positioned and assigned a z-index value other than auto, or when an element has an opacity value less than 1. In WebKit and Chrome 22+ an element with a fixed position always creates a stacking context, even when the z-index value is auto. In addition to these properties and values, newer CSS properties and values, such as transform with a value other than none, also create stacking contexts.
40. Is there any reason you'd want to use `translate()` instead of `absolute` positioning, or `vice-versa` ? And why ?
- Using transform: translate(x,y); greatly decreases paint times on elements with CSS transitions.
- below reason to use translate over absolute:
    1. Use CSS keyframe animation or CSS transitions, if at all possible. The browser can optimize painting and compositing bigtime here.
    2. If needs to be it’s JS-based animation, use requestAnimationFrame. Avoid setTimeout, setInterval.
    3. Avoid changing inline styles on every frame (jQuery animate()-style) if you can, declarative animations in CSS can be optimized by the browser way more.
    4. Using 2D transforms instead of absolute positioning will typically provide better FPS by way of smaller paint times and smoother animation
    5. Use Timeline Frame’s mode to investigate what is slowing down your behavior “Show Paint Rects” and “Render Composited Layer Borders” are good pro-moves to verify where your element is being rendered.