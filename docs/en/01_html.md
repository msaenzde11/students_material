# 01. Introduction to HTML

HTML defines the content of every web page on the Internet. By using HTML, you define the structure of your website and tell the browser how to build the website. Creating an HTML document with properly marked up content is the first step of developing a web page.

?> HTML stands for **HyperText Markup Language** and it is used to add and structure information we want in our webpage. It includes tags, attributes and flags that help structure content.

Creating a website with only HTML will not look good, because the styles are defined with CSS. It will not be very interactive, because advanced interaction is defined with javascript. HTML defines the structure.

When a web page is loaded, the browser creates a [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) (Document Object Model). This only means that the browser creates its own image of how our page looks like based on how we structure HTML. The browser will transform your HTML to its own language, so its important how we write our HTML so the browser can understand it.

## Basic HTML structure


This is the basic structure of an HTML page

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Your HTML page</title>
    </head>
    <body>
        <h1>Welcome to HTML!</h1>
    </body>
</html>
``` 

Let's read it:

1. First, we need to tell browsers that this is an HTML5 web page with the `<!DOCTYPE html>` line.
1. Then, our entire web page needs to be wrapped in `<html>` tags. Ensure that the tag is opened (`<html>`) and closed (`</html>)`. Everything inside this tag will be our HTML page.
1. Then, the HTML is divided in two tags: `head` and `body`
    1. `Head`: A web page’s head contains all of its metadata, like the page title, any CSS stylesheets, and other things that are required to render the page but you don’t necessarily want the user to see.
    1. The bulk of our HTML markup will live in the <body> element, which represents the visible content of the page.

## HTML elements

Every piece of website content is 'wrapped' in an HTML element. An HTML element is usually composed of two tags, an opening tag and a closing tag (though we will see there are exceptions). Content, such as text or other HTML elements, will be displayed within these tags. Tags have associated behaviours of the elements. Attributes can modify default behaviour of the element, or add extra information.

This is how a tag looks like. There is no `name` tag, this is just an example:

```html
 <name attribute="value">Content</name>
 ```

 This is a _paragraph_ tag with an attribute and a value, for instance. We will see more tags later:

 ```html
 <p lang="es">Párrafo</p>
 ```

### Nested tags

Tags can be nested inside of other tags. To maintain readable code, the parent tags (the outer most ones) should each be on a new line with the nested element indented. Example:

```html
<div>
  <h1>Title</h1>
  <p>Text</p>
</div>
```

Don't worry about the tags, we will learn tags in the next class.

## Comments

Comments are parts of our HTML that will not be visible to the user. It is used to write messages for the programmer of the website. A comment looks like this:

```html
    <!-- This won't be visible but will be in our code -->
```

## Hands on!

Create a new file `index.html` and add the previous HTML. Play with it: add tags, add comments and open it in your browser to see how it looks. 

It is your first website!

# 02. HTML structure and basic tags

Let's review the basic HTML structure again

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Your HTML page</title>
    </head>
    <body>
        <h1>Welcome to HTML!</h1>
    </body>
</html>
```

We are going to review a lot of tags, so try to create these tags on your HTML file along:

## `<html>` tag

This tag open and closes our HTML document. Every code should go nested in this tag.

## `<head>` tag

This tags gives the browser information that is not visible to te user.

### `<title>` tag

This tag is nested inside the `head` tag. Its function is to tell the browser the title of our website

### `<meta>` tags

This tag is nested inside the `head` tag. its function is to give information to the browser about our website (author, description, robots, language, etc.)

There are many more tags available inside the `head` tag. You can check a lot of the available tags in the `head` tag in [https://gethead.info/](https://gethead.info/)

## HTML Landmarks

HTML landmarks are tags in your page to define areas like the main content or a navigation region. It defines semantically the website and also helps users using assitive technologies to navigate comfortably through the website. 

?> Landmarks define the outer structure of our website, defining the areas of the page based on its responsibility

### `<main>` tag

The HTML `<main>` element represents the dominant content of the `<body>` of a document. The main content area consists of content that is directly related to or expands upon the central topic of a document, or the central functionality of an application.

### `<header>` tag

The HTML `<header>` element represents introductory content, typically a group of introductory or navigational aids. It may contain some heading elements but also a logo, a search form, an author name, and other elements.

### `<nav>` tag

The HTML `<nav>` element represents a section of a page whose purpose is to provide navigation links, either within the current document or to other documents. Common examples of navigation sections are menus, tables of contents, and indexes.

### `<section>` tag

The HTML `<section>` element represents a standalone section — which doesn't have a more specific semantic element to represent it — contained within an HTML document.

### `<article>` tag

The HTML `<article>` element represents a self-contained composition in a document, page, application, or site, which is intended to be independently distributable or reusable (e.g., in syndication). Examples include: a forum post, a magazine or newspaper article, or a blog entry.

### `<aside>` tag

The HTML `<aside>` element represents a portion of a document whose content is only indirectly related to the document's main content.

### `<footer>` tag

The HTML `<footer>` element represents a footer for its nearest `<section>`. A footer typically contains information about the author of the section, copyright data or links to related documents

## HTML tags

One of HTML's main jobs is to give text structure and meaning (also known as semantics) so that a browser can display it correctly. This article explains the way HTML can be used to structure a page of text by adding headings and paragraphs, emphasizing words, creating lists, and more.

### Heading `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`

Structured content makes the reading experience easier and more enjoyable.
There are six heading elements — `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, and `<h6>`. Each element represents a different level of content in the document; `<h1>` represents the main heading, `<h2>` represents subheadings, `<h3>` represents sub-subheadings, and so on.

Preferably you should just use a single `<h1>` per page — this is the top level heading, and all others sit below this in the hierarchy.

Headings should be displayed in correct order in a hierarchy. Don't use `h3` before an `h2`

### Paragraph `<p>`

In HTML, each paragraph has to be wrapped in a `<p>` element.

### Unordered lists `<ul>` and Ordered lists `<ol>`

Unordered lists are used to mark up lists of items for which the order of the items doesn't matter.

Ordered lists are lists in which the order of the items does matter.

Each bullet point in a list should be a list item `<li>`

```html
<ul>
  <li>milk</li>
  <li>eggs</li>
  <li>bread</li>
  <li>hummus</li>
</ul>
```

Lists can be nested

```html
<ol>
  <li>Remove the skin from the garlic, and chop coarsely.</li>
  <li>Remove all the seeds and stalk from the pepper, and chop coarsely.</li>
  <li>Add all the ingredients into a food processor.</li>
  <li>Process all the ingredients into a paste.
    <ul>
      <li>If you want a coarse "chunky" hummus, process it for a short time.</li>
      <li>If you want a smooth hummus, process it for a longer time.</li>
    </ul>
  </li>
</ol>
```

### Strong importance `<strong>`

In HTML we use the `<strong>` (strong importance) element to mark up important words that need to be stressed out.

```html
<p>This liquid is <strong>highly toxic</strong>.</p>
```

## Nested Elements

Tags can be nested inside of other tags. To maintain readable code, the parent tags (the outer most ones) should each be on a new line with the nested element indented.

```html
<section>
  <h1>Title</h1>
  <p>Text</p>
</section>
```

## HTML validation

HTML should be validated to ensure that we are writing 100% valid HTML. HTML is standarized by the W3C and has an available validator at [W3C - Markup Validation Service](https://validator.w3.org)

## Hands on!

Using the html structure, some of the landmarks, and the html elements learned, create a text-only page with your curriculum Vitar. Remember to be exhaustive describing every part of your CV!

Remember it should include an introduction, skills, experience, strong importance text, some info about your hobbies...etx.

Ensure that your code is validated though the W3C.

# 03. HTML advanced elements and properties

We've already learned som of the most important HTML tags. Let's see some more HTML, review how to use them and lear how to use properties.

## HTML attributes

An attribute extends a tag, changing its behavior or providing metadata. An attribute always has the form name=value (the attribute's identifier followed by its associated value).

```html
<main id="page-site">
    <h1 class="title">Page title</h1>
</main>
```

Some common HTML attributes are:

- **id**: Defines a unique identifier (ID) which must be unique in the whole document.
- **class**: A space-separated list of the classes of the element. Classes allows CSS and JavaScript to select.
- **hidden**: An attribute indicates that the element is not yet, or is no longer, relevant.
- **title**: Contains a text representing advisory information related to the element it belongs to.

Some tags have specific attributes that should only be used in that tag.

## Hyperlinks

A basic link is created by wrapping the text (or other content, see Block level links) you want to turn into a link inside an `<a>` element, and giving it an href attribute (also known as a Hypertext Reference , or target) that will contain the web address you want the link to point to.

```html
<a href="https://madridforrefugees.org/en/the-organisation/mfr-coding/">MFR Coding website</a>.
```

**Absolute and relative paths** Hyperlink tags can link to both parts of your own page, or to external pages.

- `href="https://madridforrefugees.org/en/the-organisation/mfr-coding/"` links to an external website.
- `href="#mfr-coding"` links to a part of your website with an attribute id with a value of `mfr-coding`
- `href="mailto:email@example.com"` will try to open your default email software to send an email to this email address.

Read more information about [Hyperlinks at MDN](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)

## Images `<img>`

The HTML `<img>` element embeds an image into the document. Formats could be _jpg_, _gif_, _png_ or _svg_.

```html
<img src="https://media.giphy.com/media/3oKIPnAiaMCws8nOsE/giphy.gif" alt="Animated image of a cat coding">
```

An `<img>` tag should include two attributes:

- **src**: The image URL. This attribute is mandatory.
- **alt**: This attribute defines a description of the image.

Read more information about [Images at MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)

## Description list `<dd>` and description term `<dt>`

The purpose of these lists is to mark up a set of items and their associated descriptions, such as terms and definitions, or questions and answers. 

```html
<dl>
  <dt>soliloquy</dt>
  <dd>In drama, where a character speaks to themselves, representing their inner thoughts or feelings and in the process relaying them to the audience (but not to other characters.)</dd>
  <dt>monologue</dt>
  <dd>In drama, where a character speaks their thoughts out loud to share them with the audience and any other characters present.</dd>
  <dt>aside</dt>
  <dd>In drama, where a character shares a comment only with the audience for humorous or dramatic effect. This is usually a feeling, thought, or piece of additional background information.</dd>
</dl>
```

## Blockquotes

This is an element that is used for quoting content from somewhere else.

### Block quotations

```html
<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
  <p>The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block
  Quotation Element</em>) indicates that the enclosed text is an extended quotation.</p>
</blockquote>
```

### Inline quotations

```html
<p>The quote element is <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">intended
for short quotations that don't require paragraph breaks.</q></p>
```

## Non semantic html tags

Sometimes you'll come across a situation where you can't find an ideal semantic element to group some items together or wrap some content. Sometimes you might want to just group a set of elements together to affect them all as a single entity with some CSS or JavaScript.

### Inline non-semantic tag `<span>`

The HTML `<span>` element is a generic inline container for phrasing content, which does not inherently represent anything.

### Block non-semantic tag `<div>`

The HTML Content Division element `<div>` is the generic container for flow content. It has no effect on the content or layout until styled using CSS. As a "pure" container, the <div> element does not inherently represent anything.

## Hands on!

Add a navigation area into your website. Link to other websites, to other parts of your site or to other pages in your website. You can also divide your website in different files and link them.

Use the tags you learned in this class to add some images, quotes, descriptions...etc.

## Advanced exercise

Create a skeleton of different webpages:
    1. A newsletter.
    2. A shopping page.
    3. A blog.  

# 04. Forms

We've covered basic HTML elements and attributes. We already know how to create static semantic HTML websites, display information, link pages..etc. Now, we will add a very important part of HTML: forms.

?> Forms are essential to interact and gather data from the user, and its very important to use semantically correct forms. The data gathered in a form is usually sent to a server, but nowadays it can be used in javascript to create interaction.

A form is made of multiple HTML elements: labels, text inputs, checkboxes, radio buttons, buttons...etc.

!> Warning: there is a lot of confussion on how to use forms, so be very careful when using information from other sources.

## Lets draw

Draw a form with the information we would like to gather:

![A form drawing](https://i1.wp.com/wp.laravel-news.com/wp-content/uploads/2016/03/form-drawing.jpg?resize=525%2C586)

## The `form` element

The HTML `<form>` element represents a document section that contains interactive controls for submitting information.

```html
<form action="url" method="post">
  <!-- More tags here -->
</form>
```

A form should contain two attributes:

- **action**: The location where the information will be submitted.
- **method**: The HTTP method to send the data, it can be GET or POST (for now, lets keep it simple, just use POST)

Some tags have specific attributes that should only be used in that tag.

## The `input` element

The HTML `<input>` element is used to create input widget forms in order to accept data from the user; a wide variety of types of input data and control widgets are available.

```html
<form action="url" method="post">
  <input type="text" name="user_name">
</form>
```

An input element should have two attributes:

- **type**: This is the most important attribute. It defines the behaviour of the input and will change how it works in differente devices.
  - **type="email"** will improve the user experience in devices to add an email
  - **type="password"** will hide the user input
  - **type="url"** will improve the user experience in devices to add an url
  - **type="number"** will improve the user experience in devices to add  number
  - **type="color"** will display a color selector
- **name**: The input's name, to identify the input in the data submitted with the form's data.
- **value**: The default value in the input
- **placeholder**: A hint of the expected value.

## The `label` element

A `label` element associates a form element with its caption, not only visually, but also programmatically.

To associate the `<label>` with an `<input>` element:

- You cane give the `<input>` an id attribute. The `<label>` then needs a `for` attribute whose value is the same as the input's id.
- You can nest the `<input>` directly inside the `<label>`, in which case the for and id attributes are not needed because the association is implicit

Examples:

```html
<form action="url" method="post">
  <div>
    <label for="name">Name:</label>
    <input type="text" id="name" name="user_name">
  </div>
</form>
```

or

```html
<form action="url" method="post">
  <div>
    <label for="name">
      Name:
      <input type="text" id="name" name="user_name">
    </label>
  </div>
</form>
```

The `<div>` elements are there to conveniently structure our code and improve legibility when we have multiple fields.

### Multiple `labels` with the same `for`

It's better not to use multiple `<label>` elements with the same `for` because it can cause problems with assistive technologies. In this case, it is recommended to use the parent `label` with nested inputs.

## The `textarea` element

The HTML `<textarea>` element represents a multi-line text input, useful when you want to allow users to enter a sizeable amount of text, for example a comment on a review or feedback form.

```html
<form action="url" method="post">
  <div>
    <label for="story">Tell how to cook your omelette:</label>
    <textarea id="story" name="story">
      First, scramble the eggs.
    </textarea>
  </div>
</form>
```

Be careful, the `<input>` tag is a self-closed tag, while `<textarea>` is a open tag. Inside a `<textarea>`, you can add the default text.

## The `button` element

The HTML `<button>` element represents a clickable button.

```html
<form action="url" method="post">
  <div>
    <button type="submit">Send</button>
  </div>
</form>
```

A `<button>` element should have one attribute:

- **type**: The type of the button:
  - **submit**: The button submits the form data to the server. This is the default if the attribute is not specified
  - **button**: The button has no default behavior. It usually will be triggered with javascript events.

## The `select` and `option` elements

The HTML `<select>` element represents a control that provides a menu of options. A `select` is composed of multiple `options`

```html
<form action="url" method="post">
  <div>
    <label for="fav-animal">Choose your favourite animal:</label>
    <select id="fav-animal" name="fav-animal">
      <option>Diplodocus</option>
      <option selected>Jellyfish</option>
      <option>Cockroach</option>
    </select>
  </div>
</form>
```

If an `option` has the selected attribute, will be the default selected value for the `select`.

## The `checkbox` input type

Elements of type `<checkbox>` are rendered by default as square boxes that are checked when activated, like you might see in an official government paper form.

```html
<form action="url" method="post">
  <fieldset>
    <legend>Choose your interests</legend>
    <div>
      <input type="checkbox" id="coding" name="interest" value="coding" checked>
      <label for="coding">Coding</label>
    </div>
    <div>
      <input type="checkbox" id="music" name="interest" value="music">
      <label for="music">Music</label>
    </div>
  </fieldset>
</form>
```

## The `radio` input type

elements of type radio  are similar to checkboxes with the singularity that only one radio button in a given group can be selected at the same time. 

```html
<form action="url" method="post">
  <fieldset>
    <legend>Choose your favorite thing in the world</legend>
    <div>
      <input type="radio" id="huey" name="drone" value="huey" checked>
      <label for="huey">Coding</label>
    </div>
    <div>
      <input type="radio" id="dewey" name="drone" value="dewey">
      <label for="dewey">Music</label>
    </div>
  </fieldset>
</form>
```

## Hands on!

Remember that we are still using HTML, so use the full potential of HTML: sections, lists, strong..etc.

### Basic exercise: contact form

Create a contact form in your website. Ask the user for: name, email, date of birth and comments.

### Advanced exercise: payment form

Create a payment form. It should ask the user for: name,email, password, card type, card number and expiration date.

## Resources

- [The HTML `form` element in MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)
- [The HTML `input` element in MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
- [The HTML `label` element in MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)
- [The HTML `button` element in MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button)