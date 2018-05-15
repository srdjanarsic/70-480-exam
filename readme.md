# 70-480 exam

## 1. Implement and manipulate document structures and objects

### 1.1 Create the document structure

#### Basic HTML template

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
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

HTML5 `video` and `audio` elements.

#### Implementing graphics with HTML5 <canvas>

#### Scalable Vector Graphics (SVG)