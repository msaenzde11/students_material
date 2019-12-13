# 01. Introduction to CSS

CSS means `Cascading Style Sheets`. With CSS we give styles to our webpage. As you remember, with HTML we create the structure of our website. Now, with CSS we will focus on how the structure 'looks'. For instance, you could alter the font, colour, size and spacing of your content, split it into multiple columns, or add animations and other decorative features.

Imagine a building construction process:
    - as we saw in the previous chapter, HTML would represent the foundation and skeleton of the buiding (the structure)
    - Now, CSS will represent how it looks: is it make of glass? is it painted in green? How big are the windows? Where will be the door? how will it be distributed?
    - In the next chapter, Javascript would be the mechanical and electrical installation (the interaction)

## Basic CSS styling

This is how CSS looks like. Don't worry if you don't understand this yet.

```css
h1 {
  color: blue;
  background-color: yellow;
  border: 1px solid black;
}

p {
  color: red;
}
```

Let's read it:

1. First, we have two selectors (`h1` and `p`). Each one will affect all `h1` and `p` tags in our page.
1. The first one will look for all `h1` tags and will apply the properties between the brackets to those tags.

    1. The first one sets the text color to blue.
    1. The second sets the background color to yellow.
    1. The third one puts a border around the header that is 1 pixel wide, solid (not dotted, or dashed, etc.), and colored black.

What will the second selector do?
Try it in your browser and see what happens. Change it and play with it.

## CSS selector

Every selector of css is composed of a selector and its attributes. There are multiple selector types and hundreds of attributes, but most of the time it will follow the same structure.

This is how a CSS selector looks like:

![CSS Sintax](./assets/css-sintax.png "CSS Sintax")

For instance

```css
p {
  color: red;
}
 ```

 This is a selector for all _paragraph_ tags in a page. It will set the text color in red.

```css
.atchung {
  background: red;
  color: white;
}
 ```

This is a selector for all html elements with an attribute class with the value _atchung_. Remember classes in HTML? This CSS selector will set all HTML tags background with this attribute to red and its text color to white. We will see this deeply later.

!> **Important**: If a property is unknown or if a value is not valid for a given property, the declaration is deemed invalid and is wholly ignored by the browser's CSS engine.

## Adding an stylesheet

There are three different ways to apply CSS to an HTML document that you'll commonly come across, some more useful than others.

### External stylesheet

An external stylesheet is when you have your CSS written in a separate file with a `.css` extension, and you reference it from an HTML `<link>` element in your `<head>` tag.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

Add an external CSS file to your page.

### Internal CSS

!> **Warning: this method is not recommended**

An internal stylesheet is where you don't have an external CSS file, but instead place your CSS inside a `<style>` element, contained inside the HTML `<head>`.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }

      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

### Inline styles

!> **Warning: this method is not recommended**

Inline styles are CSS declarations that affect one element only, contained within a style attribute

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
  </head>
  <body>
    <h1 style="color: blue;background-color: yellow;border: 1px solid black;">Hello World!</h1>
    <p style="color:red;">This is my first CSS example</p>
  </body>
</html>
```

Please don't do this, unless you really have to!

## Comments

Comments are parts of our CSS that will not affect the HTML. It is used to write messages for the programmer of the website. A comment looks like this

```css
    /* This is a CSS comment */
```

## Hands on

Create a new file `style.css` in a folder named styles next to your `index.html` and link the external CSS and the HTML. Add some styles to your HTML by creating selectors and properties. Just for fun, see what you can do. If you don't know CSS attributes, search online.

Style your website!!

# 02. CSS selectors

In CSS, selectors are used to target the HTML elements on our web pages that we want to style. There are a wide variety of CSS selectors available, allowing for fine grained precision when selecting elements to style. It could target tags by its name, id, class, attributes...etc.

## Selectors

### Tag selectors

This type of selector is the simplest one. Will match the name of the HTML with the name of the selector

```html
<p>What color do you like?</p>
<div>I like blue.</div>
<p>I prefer BLACK!</p>
```

```css
/* All p elements look red */
p {
  color: red;
}

/* All div elements look blue */
div {
  color: blue;
}
```

### Class selectors

As you probably remember, a class is an attribute that we can set in an HTML element.
To target a class, the selector should have a `.` before the name of the class. It is up to you to choose a name for the class, but remember, it should be a string of a single word (it can have `-` or `_`).

**Important** Multiple elements in a document can have the same class value, and a single element can have multiple class names separated by white space.

```html
<ul>
  <li class="first done">Create an HTML document</li>
  <li class="second done">Create a CSS style sheet</li>
  <li class="third">Link them all together</li>
</ul>
```

```css
/* The element with the class "first" is bolded */
.first {
  font-weight: bold;
}

/* All the elements with the class "done" are strikethrough */
.done {
  text-decoration: line-through;
}
```

### ID selectors

An ID is an attribute that we can set in an HTML element. Any element can have a unique ID name set with the id attribute. It is up to you to choose an ID name.
To target an ID we should ise a hash symbol (#), followed by the ID name of a given element.

**Warning** IDs are unique, if you duplicate an ID in HTML or CSS, results are unpredictable.

```html
<p id="polite"> — "Good morning."</p>
<p id="rude"> — "Go away!"</p>
```

```css
#polite {
  font-family: cursive;
}

#rude {
  font-family: monospace;
  text-transform: uppercase;
}
```

### Attribute selector

As you probably remember, an HTML element can have attributes.
Attribute selectors are a special kind of selector that will match elements based on their attributes and attribute values.

```html
<div>
  <img src="image1.jpg">
  <img src="image2.jpg" alt="">
  <img src="image3.jpg" alt="This is a nice image description">
</div>
```

```css
/* All `img` elements are given green border */
img {
  border: 4px green dashed;
}

/* All `img` elements that have and `alt=""` attribute are given yellow border */
img[alt=""] {
  border: 4px yellow dashed;
}

/* All `img` elements that DO NOT have and `alt` attribute are given red border */
img:not([alt]) {
  border: 4px red dashed;
}
```

### Pseudo-class selector

A CSS pseudo-class is a keyword added to the end of a selector, preceded by a colon (:), which is used to specify that you want to style the selected element but only when it is in a certain state.

For example, you might want to style a link element only when it is being hovered over by the mouse pointer

```css
.first {
  font-weight: bold;
}

.first:hover {
  font-weight: bold;
}
```

There are many pseudo-classes, some of the most important are:

- [:empty](https://developer.mozilla.org/en-US/docs/Web/CSS/:empty)
- [:not](https://developer.mozilla.org/en-US/docs/Web/CSS/:not)
- [:active](https://developer.mozilla.org/en-US/docs/Web/CSS/:active)
- [:hover](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)
- [:disabled](https://developer.mozilla.org/en-US/docs/Web/CSS/:disabled)
- [:checked](https://developer.mozilla.org/en-US/docs/Web/CSS/:checked)
- [:first-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:first-child)
- [:last-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:last-child)
- [:nth-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child)

## Combinating selectors

Selectors are useful, but are much more powerful when you combine them.

### Multiple selector combination

If the same property is being applied to many selector, we can combine them using the comma (,). Same properties will apply to all the selectors.

```css
h1, h2, h3 {
  background: black;
  color: white
}
```

### Descendant combination

Will apply to element matching `.child` that is a descendant of an element matching `.parent` no matter how deep is nested.

```css
.parent .child {
  background: black;
  color: white
}
```

```html
<section class="parent">
  <ul>
    <li>Element</li>
    <li class="child">Element</li>
    <li>Element</li>
  </ul>
</section>
```

### Universal selector

!> **Warning** Use with caution, this can make your website slow

This selector will apply to everything.

```css
* {
  background: black;
  color: white
}
```

?> There are many more selectors! Check all of them here: [https://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048](https://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048)

## Hands on

Learn to use CSS selectors:

  1. Copy the content of the file `selectors.html`
  2. Link an external stylesheet named `selectors.css`
    * Give the `<body>` element a background of `#bdc3c7`
    * Give the `<h1>` element a color of `#9b59b6`
    * Make all `<h2>` elements orange
    * Make all `<li>` elements blue
    * Change the background on every paragraph to be yellow
    * Give everything with the class `'hello'` a white background
    * Give the element with id `'special'` a 2px solid blue border
    * Make only inputs with type 'text' have a gray background
    * Make all the `<p>` that are nested inside of `<div>` 25px font
    * Make all "checked" checkboxes have a left margin of 50px

## Hands on: advanced

You may need to research some other selectors and properties
Based on this HTML:

```html
<ul>
  <li><a href="#">Colombia</a></li>
  <li><a href="#">Venezuela</a></li>
  <li><a href="#">Uruguay</a></li>
  <li><a href="#">Argentina</a></li>
  <li><a href="#">España</a></li>
  <li><a href="#">Paraguay</a></li>
  <li><a href="#">Ecuador</a></li>
</ul>
```

And this incomplete CSS (note the `____` selector)

```css
ul {
  padding: 0;
}

li {
  padding: 3px;
  margin-bottom: 5px;
  list-style-type: none;
}

a {
  text-decoration: none;
  color: black;
}

____{
  text-decoration: underline;
  color: red;
}

____ {
  background-color: #ccc;
}

____ {
  background-color: #eee;
}
```

1. Change `____` and write the required selector to create a zebra-stripped list
1. Change the style on the links to display an underline on hover.

# 03. CSS box model and units

?> Every HTML element is is represented as a rectangular box, with the box's content, padding, border, and margin built up around one another like the layers of an onion. Before understanding how to create CSS layouts, you need to understand the box model.

## CSS Box model

![CSS box model](./assets/css-box-model.png "CSS box model")
![CSS box model](./assets/box-model.png "CSS box model")

Let's review it:

### Width and height

The `width` and `height` properties set the width and height of the **content box**, which is the area in which the content of the box is displayed.

!> **Note** At the end of this document, we will change this behaviour

```css
.box {
  width: 200px;
  height: 400px;
}
```

### Padding

Padding refers to the inner margin of a CSS box — between the outer edge of the content box and the inner edge of the border.

```css
.box {
  padding: 2rem;
}
```

### Border

The border of a CSS box sits between the outer edge of the padding and the inner edge of the margin. By default the border has a size of 0 — making it invisible.

```css
.box {
  border: 2px solid red;
}
```

### Margin

The margin surrounds a CSS box, and pushes up against other CSS boxes in the layout. Like the padding, but external to the border.

```css
.box {
  margin: 2rem;
}
```

## CSS Units

Some CSS attributes require a unit value. Some that you might come across already is the pixel value (px) or the percentage (%). There are many, we will review the most important.

### Absolute numeric values

Absolute numberic values will always be the same size regardless of any other related settings like the screen or viewport.

!> **Pixels** Used the be the value of every point in a screen, but due to the advent of advanced screens, is a complicated measure depending of your screen resolution. Anyway, a pixel will always be a pixel and will not be affected by other elements. Is the most commonly used unit for absolute units.

```css
.box {
  margin: 200px;
}
```

### Relative numeric values

Relative numberic values will change depending on other variables. It can change based on the system font-size or the viewport width, for example.

- **rem**: A `rem` will be the value of the default value of the browser font-size. By default, a browsers font-size will be `16px`. So, if the user do not change the default value, a REM equals 16px.

- **em**: A `em` is similar to the `rem` but only refered to the current element. If no element has set a font-size value, then it will fallback to root value (16px).

- **vw, vh**: Viewport width and viewport height. Respectively these are 1/100th of the width of the viewport, and 1/100th of the height of the viewport.

```css
.box {
  margin: 2rem;
  width: 30vw;
  height: 10vh;
}
```

### Unitless

If the value of an attribute is zero, you might see it without any values. This is not a mistake, but a good and common practice

```css
.box {
  margin: 0;
  width: 0;
  height: 0;
}
```

### Percentage

A percentage will take the percentage size of the parent container.

```css
.parent {
  width: 200px;
  height: 300px;
}

.child {
  width: 50%;
  height: 50%;
}
```

## Box model again

As we saw at the beggining of this chapter, the **actual** width and height of a box will be

?> Width = Content-box + padding + border + margin

So if we do this:

```css
.box {
  width: 200px;
  border: 1px solid green;
  padding: 1rem;
  margin: 2rem;
}
```

The actual rendered width would be

?> width = 200px + 1rem + 1px + 2rem

Hard to calculate, isn't it?

To avoid confusion, most of the developers change the default browser behaviour

### Box-sizing

`box-sizing` is a CSS property that sets how the total width and height of an element is calculated.
When we set the value of `box-sizing` to `border-box` the final calculation will differ. The width and height properties will include the content, padding, and border, but do not include the margin.

For example:

```css
.box {
  width: 200px;
  border: 1px solid green;
  padding: 1rem;
  margin: 2rem;
}
```

The actual rendered width would be 200px and will contain the border and the padding. And will have `2rem` margin.

To do this, most of the developers will use the universal selector

```css
* {
  box-sizing: border-box;
}
```

This is a very common feature, but has to be used carefully because changes the default behaviour of the box model of EVERY element.

Last example

```css
div {
  width: 160px;
  height: 80px;
  padding: 20px;
  border: 8px solid red;
  background: yellow;
}

.content-box { 
  box-sizing: content-box;
  /* Total width: 160px + (2 * 20px) + (2 * 8px) = 216px
     Total height: 80px + (2 * 20px) + (2 * 8px) = 136px
     Content box width: 160px
     Content box height: 80px */
}

.border-box {
  box-sizing: border-box;
  /* Total width: 160px
     Total height: 80px
     Content box width: 160px - (2 * 20px) - (2 * 8px) = 104px
     Content box height: 80px - (2 * 20px) - (2 * 8px) = 24px */
}
```

# 04. CSS cascade and inheritance

## Source order

?> As mentioned above, if multiple competing selectors have the same importance and specificity, the third factor that comes into play to help decide which rule wins is source order — later rules will win over earlier rules.

```css
p {
  color: blue;
}

/* This rule will win over the first one */
p {
  color: red;
}
```

## Specificity

Specificity is basically a measure of how specific a selector is — how many elements it could match. As shown in the example seen above, element selectors have low specificity. Class selectors have a higher specificity, so will win against element selectors. ID selectors have an even higher specificity, so will win against class selectors. 

## !important

In CSS, there is a special piece of syntax you can use to make sure that a certain declaration will always win over all others: !important.

```css
.box {
  background-color: gray;
  border: none !important;
}
```

# Inheritance

## Mixing selectors

When several CSS rules match the same element, they are all applied to that element. Only after that are any conflicting properties evaluated to see which individual styles will win over others.

```css
p {
  color: blue;
}

p {
  margin: 2px;
}
/* Result will be the sum of both selectors  */
```

## Removing inheritance

### `initial` property

Sets the property value applied to a selected element to be the same as the value set for that element in the browser's default style sheet. If no value is set by the browser's default style sheet and the property is naturally inherited, then the property value is set to inherit instead.

```css
a {
  color: initial;
}
```

# 05. CSS layout

CSS page layout techniques allow us to take elements contained in a web page and control where they are positioned relative to their default position in normal layout flow.

## Default layout flow: inline vs. block

Normal flow is how the browser lays out HTML pages by default when you do nothing to control page layout.

?> The elements that appear one below the other are described as **block elements**, in contrast to **inline elements**, which appear one beside the other, like the individual words in a paragraph.

### Block

By default, a block level element's content is 100% of the width of its parent element, and as tall as its content. Each one will appear on a new line below the last one, and they will be separated by any margin that is set on them (defauylt margin or any margin we set on CSS).

```html
<h1>Basic document flow</h1>
<p>I am a basic block level element. My adjacent block level elements sit on new lines below me.</p>
<p>By default we span 100% of the width of our parent element, and we are as tall as our child content. Our total width and height is our content + padding + border width/height.</p>
```

All this elements will appear on a different lines. Each one will sit in top of the other.

### Inline

Inline elements are as tall as their content, and as wide as their content.
Inline elements don't appear on new lines as block elements; instead, they sit on the same line as one another, as long as there is space for them to do so inside the width of the parent block level element. If there isn't space, then the overflowing text or elements will move down to a new line.

```html
<p><strong>By default we span 100% of the width of our parent element</strong>, <span>and we are as tall</span> <cite>as our child content.</cite> <em>Our total width and height</em> <a href="#">is our content + padding + border width/height.</a></p>
```

All this elements will appear on the same line inside the block element `<p>`

## Positioning

Positioning allows you to take elements out of the normal document layout flow, and make them behave differently; for example sitting on top of one another, or always remaining in the same place inside the browser viewport.

### Static

This is the default value.

?> The element is positioned according to the normal flow of the document. The top, right, bottom, left, and z-index properties have no effect.

### Relative

?> The element is positioned according to the normal flow of the document, and then offset relative to itself based on the values of top, right, bottom, and left. **The offset does not affect the position of any other elements**; thus, the space given for the element in the page layout is the same as if position were static.

This is very similar to static positioning, except that once the positioned element has taken its place in the normal layout flow, you can then modify its final position, including making it overlap other elements on the page.

`top`, `bottom`, `left`, and `right` are used alongside position to specify exactly where to move the positioned element to.

```css
.box {
    position: relative;
    top: 5px;
    left: 5px;
}
```

![Position: relative](./assets/position-relative.png "Position: relative")

### Absolute

?> The element is removed from the normal document flow, and no space is created for the element in the page layout. An absolutely positioned element no longer exists in the normal document layout flow. Instead, it sits on its own layer separate from everything else. This is very useful: it means that we can create isolated UI features that don't interfere with the position of other elements on the page. For example: popups, dialogs, floating menus...etc.

`top`, `bottom`, `left`, and `right` are used alongside position to specify exactly where to move the positioned element to.

!> **IMPORTANT: The box will be positioned relative to its closest positioned ancestor**, if any. What is a positioned ancestor? The nearest ancestor element that has a position value other than static (fixed, absolute, relative, or sticky). If no ancestor elements have their position property explicitly defined the box will be positioned relatively to the html element.

```css
.box {
  position: absolute;
  background: yellow;
  top: 30px;
  left: 30px;
}
```

![Position: absolute](./assets/position-absolute.png "Position: absolute")

### Fixed

?> The element is removed from the normal document flow, and no space is created for the element in the page layout. It is positioned relative to the initial containing block. Its final position is determined by the values of top, right, bottom, and left.

This works in exactly the same way as absolute positioning, with one key difference: whereas absolute positioning fixes an element in place relative to the `<html>` element or its nearest positioned ancestor, **fixed positioning fixes an element in place relative to the browser viewport itself**.

```css
.box {
  position: fixed;
  top: 0;
  width: 500px;
  margin: 0 auto;
  background: white;
  padding: 10px;
}
```

![Position: fixed](./assets/position-fixed.png "Position: fixed")

### Sticky

?> The element is positioned according to the normal flow of the document, and then offset relative to its nearest scrolling ancestor and containing block

Using this type of position, en element will be positioned as its position is `relative` until the paige is scrolled to a certain threshold point (e.g. 10px from the top of the viewport), after which it becomes `fixed`.

```css
.box {
  position: sticky;
  top: 30px;
  left: 30px;
}
```

![Position: sticky01](./assets/position-sticky01.png "Position: sticky")
![Position: sticky02](./assets/position-sticky02.png "Position: sticky")

## Flexbox

The main aim of flexbox is to craft one-dimensional layout structures (vertical or horizontal). Items in flex layouts will shrink or grow to fill the space available and will position relative to the parent container.

!> **Important** Although multi-dimensional grids can be accomplished by using flexbox, it is recommended to craft those layouts using [grid layouts](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids).

!> **Important** Flexbox is relativelly new. Before flexbox, the only way to create CSS layouts were [floats](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Floats). Although can be seen nowadays is strongly discouraged.

Please note that there is a difference between the parent container (flex container) and its children (flex children). Focus first on the parent properties that affect all children and then change children properties if needed.

### Flex element

To start with, we need to select which elements are to be laid out as flexible boxes. To do this, we set a special value of display on the parent element of the elements you want to affect.

```css
.box {
  display: flex;
}
```

The `.box` container will turn into a flex container and all its child elements will layout in columns, each one the same size.

![Flexbox](./assets/flexbox-example.png "Flexbox")

#### Layout direction

By default, elements in a flex container will be set to `row` (horizontal) but we can alter the element position changing its `flex-direction` property to `column` (vertical)

```css
.box {
  display: flex;
  flex-direction: column;
}
```

#### Layout alignment

You can use flexbox to align the childrens of the parent element.

- **Align items** will align the items on vertical axis.
  - **stretch** This is the default value. Will stretch all items to meet the parent height.
  - **center** Will center all items vertically.
  - **flex-start** Will align items to the beggining of the parent.
  - **flex-end** Will align items to the end of the parent.

- **Justify content** will align the items on horizontal axis.
  - **flex-start** This is the default value.  Will align items to the beggining of the parent.
  - **flex-end** Will align items to the end of the parent.
  - **center** Will center all items horizontally.
  - **space-between** Will layout the items in the full width of the parents but will not grow the width of the children and leaves some space at the end.
  - **space-around** Will layout the items in the full width of the parents separated  but will not grow the width of the children.

Since this might be a complicated (and a bit abstact) explanation, read this interesting resources:

- [A guide to flexbox by **CSS tricks**](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Flexbox Froggy: a game to learn flexbox](https://flexboxfroggy.com/)

### Flex children

Do you remember the parent flex container, don't you? Each of the child elements has been laid out as flexible, each one the same size.

#### Flex property

The flex property is a unitless proportion value that dictates how much of the available space each flex item will take up.

```css
.box-child:nth-child(2) {
  flex: 2;
}
```

In this example, the second element will take up twice as much of the available width as the other elements. Imagine we have three elements. The fist and the third one will take now 1/4 of the available space each, while the second will take the double (1/2). Note that, by default, each element has a flex value of 1.

Actually, flex property is just a shorthand of the properties.

- Flex-grow: The unitless proportion value we discussed above.
- Flex-shrink: The opposite, how much an element can shrink if the container is too small.
- Flex-basis: Minimum size value inside the flex value. Like a fallback, sets the minimum size of an element.

```css
.box-child:nth-child(2) {
  /* flex: 1; */
  flex-grow: 1; /* Will take a proportional part if parent grows */
  flex-shrink: 1; /* Will shrink a proportional part if parent shrinks */
  flex-basis: auto; /* Minimum size of the box (can grow) */
}
```

# 06. CSS responsive

It is fairly common to create a Web site or app that changes its user interface depending on the browser or device accessing the site to provide an optimized experience.

?> Developers usually create a single version of the website which doesn't care about what browser or platform is accessing the site, but instead uses feature tests to find out what code features the browser supports or what the values of certain browser features are, and then adjusts the code appropriately.

## Fluid Grids

First approach to start is with fluid measurements for our application layout (using flexible units (rem, percentages) instead of absolute(px)). This has a lot of advantages in that the layout will adapt to different viewport dimensions.

> **Exercise** Build an example of a fluid layout

## Mobile first

At implementation stage, we present the mobile layout and functionality as the default configuration provided, before additional information is loaded on top of that, whenever appropriate. This means that mobiles (often the target devices with the least available member, bandwidth or processing power available) can be given an experience suitable for them as quickly as possible, and as free as possible of extraneous information.

?> This methodology of building a version for the relatively lower browser is called **progressive enhancement**

**Mobile first**, as the name suggests, means that we start the product design from the mobile end which has more restrictions, then expand its features to create a tablet or desktop version.

## DevTools responsive mode

With Responsive Design Mode enabled, the content area for web pages is set to the screen size for the particular device. Initially, it's set to 320 x 480 pixels.

The most obvious factor here is screen size, but there are other factors as well, including the pixel density of the display and whether it supports touch. Responsive Design Mode gives you a simple way to simulate these factors, to test how your website will look and behave on different devices.

Open your developer tools and find the `responsive mode`. It could be displayed a simple icon looking like a mobile phone.

## Media queries

Fluid grids are a great start, but you'll notice that at certain points (known as breakpoints) the layout starts to break down. At these points you'll want to change the layout to rectify the layout problem, and this can be done using media queries.

**Media queries** let you adapt your site or app depending on the presence or value of various device characteristics and parameters.

```css
.box {
    width: 75%;
}

@media all and (max-width: 1024px) {
  .box {
      width: 50%;
  }
}
```

### Media features

Media features describe specific characteristics of the user agent, output device, or environment. When selecting our media query we can target the device based on multipe parameters

- Width of the viewport (`width`, `max-width` or `min-width`) *Most used query*
- Height of the viewport (`height`, `max-height` or `min-height`)
- Aspect ratio of the viewport (`aspect-ratio: 4/3`)
- Orientation of the device (`portrait` or `landscape`)
- And [many more features](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Media_features)

### Media operators

The logical operators `not`, `and`, and `only` can be used to compose a complex media query. You will probably use the `and` operator.

```css
@media (min-width: 30em) and (orientation: landscape) {
  .box {
      width: 50%;
  }
}
```

# 07. CSS transitions and animations

It is common when developing a website to add some interactive information using transitions or animations to improve the user experience and display some beuatiful interactions.

Developers use two different techniches depending on what type of animation do they need: CSS transitions and CSS animations. While CSS transitions are somehow animations, these are much simpler tha the latter. Animations can be very advanced.

## Transitions

CSS Transitions is a module of CSS that lets you create gradual transitions between the values of specific CSS properties. The behavior of these transitions can be controlled by specifying their timing function, duration, and other attributes.

?> For example, if you change the color of an element from white to black, usually the change is instantaneous. With CSS transitions enabled, changes occur at time intervals that follow an acceleration curve, all of which can be customized.

CSS transitions let you decide which properties to animate (by listing them explicitly), when the animation will start (by setting a delay), how long the transition will last (by setting a duration), and how the transition will run (by defining a timing function, e.g. linearly or quick at the beginning, slow at the end).

```css
[selector] {
  transition: <property> <duration> <timing-function> <delay>;
}
```

### transition-property

The transition-property sets the CSS properties to which a transition effect should be applied.

```css
[selector] {
  transition-property: margin-right, color;
}
```

```css
[selector] {
  transition-property: all;
}
```

### transition-duration

The transition-duration CSS property sets the length of time a transition animation should take to complete. By default, the value is 0s, meaning that no animation will occur.

The transition value usually is set in milliseconds `ms` or `s`

```css
[selector] {
  transition-property: margin-right, color;
  transition-duration: 500ms;
}
```

### transition-timing-function

The transition-timing-function CSS property sets how intermediate values are calculated for CSS properties being affected by a transition effect.

This, in essence, lets you establish an acceleration curve so that the speed of the transition can vary over its duration.

```css
[selector] {
  transition-timing-function: ease-in;
}
```

Posible values are:

- transition-timing-function: ease;
- transition-timing-function: ease-in;
- transition-timing-function: ease-out;
- transition-timing-function: ease-in-out;
- transition-timing-function: linear;
- transition-timing-function: step-start;
- transition-timing-function: step-end;

### transition-delay

The transition-delay property specifies the duration to wait before starting a property's transition effect when its value changes.

```css
[selector] {
  transition-property: color;
  transition-delay: 250ms;
}
```

## Animations

CSS Animations is a module of CSS that lets you animate the values of CSS properties over time, using keyframes. The behavior of these keyframe animations can be controlled by specifying their timing function, duration, their number of repetitions, and other attributes.

Animations consist of two components, a style describing the CSS animation and a set of keyframes that indicate the start and end states of the animation’s style, as well as possible intermediate waypoints.

### Animation property

The animation property is the shorthand for multiple animation values

```css
[selector] {
  /* @keyframes duration | timing-function | delay | name */
  animation: 3s linear 1s slidein;
}
```

#### animation-name

The animation-name CSS property sets one or more animations to apply to an element. The name has to be the same of the `@keyframes`

```css
[selector] {
  animation-name: slidein;
}

@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```

#### animation-duration

The animation-duration CSS property sets the length of time that an animation takes to complete one cycle.

```css
[selector] {
  animation-name: slidein;
  animation-duration: 3s;
}
```

#### animation-timing-function

The animation-timing-function CSS property sets how an animation progresses through the duration of each cycle.

```css
[selector] {
  animation-name: slidein;
  animation-timing-function: ease-in-out;
}
```

#### animation-delay

The animation-delay CSS property sets when an animation starts. 

```css
[selector] {
  animation-name: slidein;
  animation-delay: 2s;
}
```

#### animation-iteration-count

Configures the number of times the animation should repeat; you can specify infinite to repeat the animation indefinitely.

```css
[selector] {
  animation-name: slidein;
  animation-iteration-count: inifinite;
}
```

#### animation-direction

The animation-direction CSS property sets whether an animation should play forwards, backwards, or alternating back and forth.

```css
[selector] {
  animation-name: slidein;
  animation-direction: alternate;
}
```

### Keyframes

Once you’ve configured the animation, you need to define the appearance of the animation. This is done by establishing two or more keyframes using the `@keyframes` at-rule. Each keyframe describes how the animated element should render at a given time during the animation sequence.

Using keyframes you can define the beggining and the end of the animation plus all the intermediate steps. Remember that the `@keyframes` name should match the animation name property.

These are similar to CSS transitions written in both valid formats

```css
@keyframes slidein {
  0% {
    margin-left: 100%;
    width: 300%;
  }

  100% {
    margin-left: 0%;
    width: 100%;
  }
}
```

```css
@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```

#### Multiple keyframes

So imagine your animation has multiple steps.

```css
@keyframes identifier {
  0% {
    top: 0;
    left: 0;
  }
  30% {
    top: 50px;
  }
  68%, 72% {
    left: 50px;
  }
  100% {
    top: 100px;
    left: 100%;
  }
}
```

In this case there are some properties that are not set in every step. That is correct, the property will interpolate until the next step where is set or finish if no more interpolations are available.
