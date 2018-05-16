# 70-480 exam

## 1. Implement and manipulate document structures and objects

### 1.1 Create the document structure

#### Basic HTML template

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8"/>
  <title></title>
</head>
<body>
   <!-- page content goes here -->
</body>
</html>
```

#### Semantic HTML

**Semantic** elements provide a stronger semantic definition to your webpages.\
**Div** for styling and it allows more dynamic capabilities in page layout.\
**Table** for more  static layouting.\
**Difference** between semantic elements and `<div>` is that `<div>` is inable to impart standard semantic meaning to each section.

|  element    | description |
|-------------|-------------|
| article     | Defines self-contained areas on a page |
| aside       | Defines smaller content areas outside the flow of a webpage |
| figcaption  | Defines the caption of a figure element |
| figure      | Defines content that contains a figure, such as an image, chart, or picture |
| footer      | Defines the bottom of a section or page |
| header      | Defines the top of a section or page |
| hgroup      | Defines a group of headings (H1–H6 elements) |
| mark        | Defines text that should be highlighted |
| nav         | Defines navigation to other pages in the site |
| progress    | Defines the progress of the task |
| section     | Defines the distinct content of a document |
| dialog      | Defines dialog box |
| filedset    | Group several controls as well as labels |
| thead, tbody, tfoot    | Gives semantic meaning to table |



#### Semantic HTML example

```html
<body>
    <header>
        <h1>Welcome to semantic webpage!</h1>
        <nav>
            <a href="home.html">Home</a>
            <a href="about.html">About</a>
        </nav>
    </header>
    <article>
        <header>
            <hgroup>
                <h1>Semantic title</h1>
                <h2>Semantic subtitle</h2>
            </hgroup>
        </header>
        <section>
            <h1>Section 1</h1>
            <p>Some
                <mark>important</mark> details about section 1</p>
            <aside>Did you know that 7/10 is 70%</aside>
        </section>
        <section>
            <h1>Section 2</h1>
            <figure>
                <img src="smile.jpg" style="width:50px; height:50px;" />
                <figcaption>Fig 1: A really nice smile.</figcaption>
            </figure>
            <p>Our goal is to have 1000 users:</p>
            <span>0</span>
            <progress value="50" max="1000"></progress>
            <span>1000</span>
        </section>
    </article>
</body>
```

#### Optimizing for search engines

Search engine optimization (SEO) is a technique used to make elements of the website easily discoverable and appropriately indexed by search engines.

The `<article>` and `<section>` elements are the main ones used by the SEO algorithm. These elements are known to contain the main body of the page. That a page have more than one `<article>` and/or `<section>` element is acceptable; they all get indexed. Within each `<article>` element, the engine then seeks out elements such as `<hgroup>` or `<h1>` to get the main topic of the `<article>` element for relevant indexing.

#### Optimizing for screen readers

Valid but not semantic.

```html
<h1>Fruits and Vegetables</h1>
<h2>Fruit</h2>
<h3>Round Fruit</h3>
<h3>Long Fruit</h3>
```

Semantic.

```html
<section>
    <h1>Fruits and Vegetables</h1>
    <section>
        <h1>Fruit</h1>
        <section>
            <h1>Round Fruit</h1>
        </section>
        <section>
            <h1>Long Fruit</h1>
        </section>
    </section>
</section>
```

The difference is that now each `<section>` element creates a new page section rather than rely on the header elements to create the sections.

#### Objective summary

* HTML5 introduced new semantic elements (some of the are listed above).
* Use `div` and `tables` for layout.
* HTML5 semantic pages are more accessibility via screen readers.
* Search engine uses `article` and other semantic tags to better understand page and creates index depend on that.

### 1.2 Write code that interacts with UI controls

#### Adding or modifying HTML elements

Modify an HTML document at run time.\
JavaScript provides the toolkit you need to write code that interacts with webpage elements after they are already rendered into the browser. Before you can start to modify the webpage, you need to know how to access or reference the elements so you can manipulate them.

#### Document Object Model

**DOM** is a representation of the structure of HTML page that you can interact with programmatically.

Behind the scenes, the browser constructs a DOM. The DOM’s application programming interface (API) is exposed as objects with properties and methods, enabling you to write JavaScript code to interact with the HTML elements rendered to the page.

#### Selecting DOM elements

| Method                 | Usage description |
|------------------------|-------------------|
| getElementById         | Gets an individual element on the page by its unique id attribute value |
| getElementsByClassName | Gets all the elements that have the specified CSS class applied to them |
| getElementsByTagName   | Gets all the elements of the page that have the specified tag name or element name |
| querySelector          | Gets the first child element found that matches the provided CSS selector criteria |
| querySelectorAll       | Gets all the child elements that match the provided CSS selector criteria |

Some methods return Element, other NodeList

*Note: `listing-1.2.html` contains examples.*

#### Altering the DOM

Commonly used methods

| Method                                          | Description    |
|----------------------------------------------------------------|----------------|
| createElement( tagName )                        | Create new node |
| parentNode.appendChild( newNode )               | Add node at the end |
| parentNode.insertBefore( newNode, refNode )     | Add node before refNode |
| parentNode.removeChild( childNode )             | Removes childNode |
| parentNode.replaceChild( newChild, oldChild )   | Replace node - oldChild with newChild |
| hasChildNodes()  | If the parent element has any child nodes at all.|

Commonly used properties

| Property       | Description    |
|----------------|----------------|
| childNodes     | A collection of all child nodes of the parent element. |
| firstChild     | A reference to the very first child node. |
| lastChild      | A reference to the very last child node. |
| parentNode | Parent of the current node (Element, Document, DocumentFragment) |

#### Implementing media controls

HTML5 `video` element

```html
<video src="video.mp4" controls poster="poster.jpg" width="800" height="600"></video>
```
Video attributes

| Attribute        | Description |
|------------------|-------------|
| src              | local or external domain video source
| autoplay         | auto play on page load
| controls         | show controls
| height/width     | set size, if omitted video displays in its original size
| loop             | play video in loop
| poster           | show poster, if not provided, first frame of video will be used

Following example shows how to setup different video formats.

```html
<video controls width="800" height="600" poster="picture.jpg">
    <source src="video.ogv" type="video/ogg"/>
    <source src="video.mp4" type="audio/mp4"/>
    <object>
        <p>Video is not supported by this browser.</p>
    </object>
</video>
```

Browser goes through source list and use first it's able to play.

|Video props/methods | Description |
|--------------|-------------|
| play()       | Plays the video from its current position.|
| pause()      | Pauses the video at its current position.|
| volume       | Allows the user to control the volume of the video.|
| currentTime  | Represents the current position of the video. |

HTML5 `audio` element

Audio element has the same properties and methods, except it has no visual representation, only in case you setup controls.

```html
<audio controls>
    <source src="audio.mp3" type="audio/mp3"/>
    <source src="audio.ogg" type="audio/ogg"/>
    <p>Your browser does not support HTML5 audio.</p>
</audio>
```

#### Implementing graphics with HTML5 `<canvas>`

You can draw lines, text, and images on the canvas and manipulate them with JavaScript.

```html
<canvas id="canvasSurface" width="800" height="600">
    Your browser does not support HTML5.
</canvas>
```

Top-left corner of the canvas is (0,0).

```js
window.onload = function () {
    var canvasSurface = document.getElementById("canvasSurface");
    var ctx = canvasSurface.getContext("2d");
}
```

You get a reference to your canvas element followed by a reference to a "2d" context. The context is an object that provides the API methods you use to draw on the canvas. 

Drawing lines

| Method      | Description  |
|-------------|--------------|
| beginPath   | Resets/begins a new drawing path |
| moveTo      | Moves the context to the point set in the beginPath method |
| lineTo      | Sets the destination end point for the line |
| stroke      | Strokes the line, which makes the line visible |
| lineWidth   | Width of line |
| strokeStyle | Line color - accept all html variation (e.g. "rgba(0,0,0,0.5)") |
| lineCap | Line ends style (butt, round, square) |
| lineJoin | Line joins style (miter, bevel, round) |

Drawing curves

| Method            | Description   |
|-------------------|---------------|
| arc               | Arc based on a starting and ending angle and a defined radius |
| quadradicCurveTo  | Complex arc that allows you to control the steepness of the curve |
| bezierCurveTo     | Complex arc that you can skew |

Arc

```js
ctx.arc(x, y, radius, startAngle, endAngle, ccw);
ctx.quadraticCurveTo(controlX, controlY, endX, endY);
ctx.bezierCurveTo(controlX, controlY, control2X, control2Y, endX, endY);
ctx.rect(x, y, width, height);
```

Fill


| Property/Method   | Description   |
|-------------------|---------------|
| fillStyle         | Fill style |
| fill              | Fill using applied fill style |
| fillRect          | Fill using applied fill style to provided rect bounds|

```js
// fill method
ctxt.fillStyle = "blue";
ctxt.fill();
// special fill method for rect
ctxt.fillStyle = "blue";
ctxt.fillRect(x, y, width, height);
```

Gradient

```js
// create gradient
ctx.createLinearGradient(x0, y0, x1, y1);
ctx.createRadialGradient(x0, y0, r0, x1, y1, r1);
// add gradiend point
addColorStop(offset, color);
// example
var gradient = ctxt.createRadialGradient(200, 200,5, 250, 250,100);
gradient.addColorStop(0, "Red");
gradient.addColorStop(.5, "Orange");
gradient.addColorStop(1, "Blue");
ctxt.fillStyle = gradient;
//
```

Pattern
```js
ctx.createPattern(image, repetition);
//image: repeat, repeat-x, repeat-y, no-repeat
```

Draw image

```js
ctx.drawImage(image, dx, dy);
ctx.drawImage(image, dx, dy, dWidth, dHeight);
ctx.drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight);
```

Drawing text

```js
// outline text
ctxt.font = "24px arial";
ctxt.strokeStyle = "Red";
ctxt.strokeText("Red colored", 100, 100);
// fill text
ctxt.font = "24px arial";
ctxt.textAlign = "center";
ctxt.fillStyle = "Blue";
ctxt.fillText("Centered text", canvas.width/2, canvas.height/2);
```

Conclusion: The canvas is a strong utility for presenting graphics dynamically in the browser.

#### Scalable Vector Graphics (SVG)

Scalable Vector Graphics (SVG) is an XML-based language for creating two-dimensional graphics. It’s implemented by using tags defined by the SVG XML namespace and embedded in HTML5 documents within opening and closing `<svg>` elements.

```html
<circle cx="50" cy="50" r="50" fill="green"/>
<rect x="100" y="100" width="60" height="200" fill="black" />
<circle cx="129" cy="265" r="25" fill="green" />
<image href="../media/men.png" width="250" height="100" />
<polygon points="10,15 30,35 10,85 100,85, 70,35,100,15" fill="purple" />
<polyline points="10,150 30,170 50,132 62,196" style="stroke:orange; fill:none; stroke-width:5;" />
<line x1="150" y1="100" x2="150" y2="150" style="stroke:blue;stroke-width:3" />
<ellipse cx="250" cy="150" rx="30" ry="55" fill="green" />
<text x="20" y="20" style="stroke: black;stroke-width:1;">Text</text>
```

### Objective 1.3: Apply styling to HTML elements programmatically

Position

```js
img.style.position = "absolute"
img.style.left = left.value + "px";
img.style.top = top.value + "px";
```

Transform

```js
transform: scale(2);
transform: rotate(90deg);
transform: skew(10deg, 10deg);
// multiply transform; NOTE: order mater
transform: translate(50px,0px) scale(1.5) skew(10deg, 10deg);
```

Show/hide and visibility

```js
el.style.display = 'inline';  // none|inline|block
el.style.visibility = 'visible'; // visible|hidden|collapse|inherit
```

`display=none` - doesn't preserve layout. elements is removed from layout, other element are rearranged.\
`visibility=hidden` - preserve layout. just hide elements.
