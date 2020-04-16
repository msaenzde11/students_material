****# 01. Custom Properties

**Custom properties** (sometimes referred to as CSS variables) are variables defined by CSS authors that contain specific values to be reused throughout a document (similar to JS variables). They are set using custom property notation (e.g., `--main-color: black;`) and are accessed using the var() function (e.g., `color: var(--main-color);`).

?> Complex websites have very large amounts of CSS, often with a lot of repeated values. For example, the same color might be used in hundreds of different places, requiring global search and replace if that color needs to change. Custom properties allow a value to be stored in one place, then referenced in multiple other places.

### Using variables

```css
.parent-element {
    --main-color: #000;
}

.child-element {
    background: var(--main-color);
}

/* Custom properties using fallback value */
.sibling-element[attr] {
    background: var(--main-color, #fff);
}

```

## Updating the value from javascript

```javascript
const element = document.querySelector('.parent-element');
element.style.setProperty("--main-color", "pink");
```

## Class naming methodology [BEM]

On smaller sites, how you organize your styles isn’t usually a big concern. However, in larger projects, how you organize your code is key. Nowadays, most of the companies use at least one method of CSS naming methodology to ensure performance, structure and maintanibility.

BEM is the abbreviation of **Block, Element, Modifier**:

- **Block**: Standalone entity that is meaningful on its own (header, menu, input),
- **Element**: A part of a block that has no standalone meaning and is semantically tied to its block. (header -> title, menu -> item)
- **Modifier**: Use them to change appearance or behavior. (header -> title -> active, menu -> item -> highlighted)

### Using BEM

```html
<button class="button">
  Normal button
</button>
<button class="button button--state-success">
  Success button
</button>
<button class="button button--state-danger">
  Danger button
</button>
```

```css
.button {
  display: inline-block;
  border-radius: 3px;
  padding: 0.5rem 0.75rem;
  border: 1px solid #D5D5D5;
  background-image: linear-gradient(#EEE, #DDD);
  font: 700 13px/18px Helvetica, arial;
}
.button--state-success {
  color: #FFF;
  background: #569E3D linear-gradient(#79D858, #569E3D) repeat-x;
  border-color: #4A993E;
}
.button--state-danger {
  color: #900;
}
```

Further reading:

- [Bem Documentation](http://getbem.com/)
- [Bem Methodology for small projects](https://www.smashingmagazine.com/2014/07/bem-methodology-for-small-projects/)

## Caniuse && Feature Queries

Not every CSS and JS feature is supported for every browser. Some projects may require to support an old version of a browser and we might not be able to use this feature. It is very important to ensure that the browsers we expect our customers are going to use are supported by our code.
"Can I use" provides up-to-date browser support tables for support of front-end web technologies on desktop and mobile web browsers.

![can I use table](./assets/caniuse.png "CanIuse Table")

For example, can I use flexbox in every browser?
No, some browsers like [Internet Explorer 11 do not support standard CSS flexbox](https://caniuse.com/#search=flexbox)

In case a browser does not support a feature, we can query if the browser does support this feature and offer an alternative:

```css

div {
    display: flex;
}

@supports (display: grid) {
  div {
    display: grid;
  }
}

```

## Exercises on FreeCodeCamp

!> These exercises are required to complete MFR coding project. Please login into your FreeCodeCamp profile to save the advance. If you have any problems, contact the teachers in [Slack](mfrcodingproject.slack.com).

1. [Use CSS Variables to change several elements at once](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/use-css-variables-to-change-several-elements-at-once)
1. [Create a custom CSS Variable](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/create-a-custom-css-variable)
1. [Use a custom CSS Variable](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/use-a-custom-css-variable)
1. [Attach a Fallback value to a CSS Variable](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/attach-a-fallback-value-to-a-css-variable)
1. [Inherit CSS Variables](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/inherit-css-variables)
1. [Change a variable for a specific area](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/change-a-variable-for-a-specific-area)
1. [Use a media query to change a variable](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/use-a-media-query-to-change-a-variable)

# 02. Sass

!> Please open this website to follow this lesson: https://www.sassmeister.com/

A CSS preprocessor is a program that lets you generate CSS from the preprocessor's own unique syntax. There are many CSS preprocessors to choose from, however most CSS preprocessors will add some features that don't exist in pure CSS, such as mixin, nesting selector, inheritance selector, and so on. These features make the CSS structure more readable and easier to maintain.

## Preprocessing

Preprocessing CSS is becoming an standard in the workflow of web development.
Preprocessing is a process in which the code we write in another language (Sass, LESS, Stylus, postCSS...etc) is converted automatically to standard CSS before being executed in our website. using a CSS preprocessor as Sass wil lgive you everything CSS has and many more things (mixins, conditionals, nesting...etc.). This features are intended to make CSS development faster and more effective

> Sass file ----> preprocessor tool ----> Standard CSS

We will be learning Sass since is the most common CSS preprocessor language but there are many:

- [Sass: Sintactically awesome Style Sheets](https://sass-lang.com/)
- [LESS](http://lesscss.org/)
- [Stylus](http://stylus-lang.com/)
- [PostCSS](https://postcss.org/)

?> Sass has two different syntaxes (sass and scss). We will use `scss` since is the most commonly used.

## Variables

Sass implements variables. Think of it as similar to custom properties, although Sass variables are less powerful because we cannot change it dynamically through javascript.

!> **WARNING:** Use custom properties instead of Sass variables if the browser supports it.

Think of variables as a way to store information that you want to reuse throughout your stylesheet. You can store things like colors, font stacks, or any CSS value you think you'll want to reuse. Sass uses the `$` symbol to make something a variable. Here's an example:

```css
$primary-color: #333;

body {
  color: $primary-color;
}

element {
  background: $primary-color;
}
```

> Execute this on `Sassmeister` to see what happens.

## Nesting

When writing HTML you've probably noticed that it has a clear nested and visual hierarchy. CSS, on the other hand, doesn't.

Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML.

```css
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }
}

```

!> **WARNING:**overly nested rules will result in over-qualified CSS that could prove hard to maintain and is generally considered bad practice.

> Execute this on `Sassmeister` to see what happens.

## Hands on

Get a CSS file from a previous project and try to convert it (or part of it) to Sass using sassmeister. Remember to include custom properties, nesting selectors, sass variables.

Can you spot difference between custom properties and sass variables?

# 03. Advanced Sass

?> To follow this part you should install a Sass compiler:

- Download and install [KoalaApp](http://koala-app.com/)
- Create a new folder named `04_advanced_ui` in your classes folder
- Create a file named `main.scss`.
- Copy and paste the code from sassmeister you just created.
- Open `Koala` and on the `+` symbol. Search the folder we just created and add it.
- You should see your `main.scss` file. Select it.
- Click on `compile` button.

This process should create two files: `main.css` and `main.map.css`. Forget about the last one for now, its just a [sourcemap](https://blog.teamtreehouse.com/introduction-source-maps)

Open you `main.css`. It should be the CSS compiled as Sassmeister did. Now you are able to compile your own files.
Remember that you should modify only on the `main.scss` but your HTML should include the automatically generated `main.css` file.

The process is the following:

1. Edit `main.scss`
2. Compile using koala.
3. Link the generated `main.css` to your html `head`
4. Confirm that the CSS works.
5. Modify and compile again `main.scss`

## Partials

CSS files on large applications can become difficult to read because they can become reaaaaaally long. Sass allows to separate the files into small chunks of code that can be imported into other files to reduce the size. Files can be separated by responsibility.

?> Architecting a CSS project is probably one of the most difficult things you will have to do in a project’s life. Keeping the architecture consistent and meaningful is even harder.

For example, a folder structure according to [Sass Guildelines](https://sass-guidelin.es/#architecture)

```bash
styles/
|
|– abstracts/
|   |– _variables.scss    # Sass Variables
|   |– _mixins.scss       # Sass Mixins
|
|– base/
|   |– _reset.scss        # Reset/normalize
|   |– _typography.scss   # Typography rules
|   …                     # Etc.
|
|– components/
|   |– _buttons.scss      # Buttons
|   |– _carousel.scss     # Carousel
|   |– _cover.scss        # Cover
|   |– _dropdown.scss     # Dropdown
|   …                     # Etc.
|
|– layout/
|   |– _navigation.scss   # Navigation
|   |– _header.scss       # Header
|   |– _footer.scss       # Footer
|   |– _sidebar.scss      # Sidebar
|   |– _forms.scss        # Forms
|   …                     # Etc.
|
|– pages/
|   |– _home.scss         # Home specific styles
|   |– _contact.scss      # Contact specific styles
|   …                     # Etc.
|
|– main.scss              # Main Sass file
```

## Import

From the main file, we can import the chunks of CSS into a single file that wil lbe compiled into a CSS file. Magic!

The `main.scss` file could look somethink like this:

```css
@import 'abstracts/variables';
@import 'abstracts/mixins';

@import 'base/reset';
@import 'base/typography';

@import 'layout/navigation';
@import 'layout/grid';
@import 'layout/header';
@import 'layout/footer';
@import 'layout/sidebar';
@import 'layout/forms';

@import 'components/buttons';
@import 'components/carousel';
@import 'components/cover';
@import 'components/dropdown';

@import 'pages/home';
@import 'pages/contact';

@import 'themes/theme';
@import 'themes/admin';
```

### Rules for import

Notice that files that ar chunks that will be imported are preceded by the simbol `_` as in `_variables.scss` but, when you import them, you should omit the underscore symbol. This symbol is telling sass that this file is just a part of a larger file and will not try to compile it.

Remember:

- one file per `@import`;
- one `@import` per line;
- no new line between two imports from the same folder;
- a new line after the last import from a folder;
- file extensions and leading underscores omitted.

### Order of imports

And remember, in CSS the order of the CSS is important. If two rules have the same name, rules will be merged and the last one will overwrite the previous one. be careful with your project naming.

## Mixins

Mixins are one of the most used features from the whole Sass language. They are the key to reusability and DRY components. And for good reason: mixins allow authors to define styles that can be reused throughout the stylesheet.

They can contain full CSS rules and pretty much everything that is allowed anywhere in a Sass document. They can even take arguments, just like functions. Needless to say, the possibilities are endless.

This is how a mixin looks like

```css
/*
// Define the mixin
// This mixin is named `size` and receives two parameters: width and height
// If the height parameter its not set, it will be equal to width
// This mixin returns a piece of CSS with width and height.
*/
@mixin size($width, $height: $width) {
  width: $width;
  height: $height;
}

/*
// And use it anywhere
*/
.box {
    @include size(1rem);
}

// Equals
/*
    width: 1rem;
.box {
    height: 1rem;
*/
```

### Argument-less mixins

A mixin might not receive arguments.

```css
@mixin large-font {
    font-family: 'Roboto', Arial;
    font-weight: 600;
    font-size: 2rem;
}

.selector {
    @include large-font;
}
```

## Exercises on FreeCodeCamp

!> These exercises are required to complete MFR coding project. Please login into your FreeCodeCamp profile to save the advance. If you have any problems, contact the teachers in [Slack](mfrcodingproject.slack.com).

1. [Create Reusable CSS with Mixins](freecodecamp.org/learn/front-end-libraries/sass/create-reusable-css-with-mixins)
1. [Use @if and @else to Add Logic To Your Styles](https://www.freecodecamp.org/learn/front-end-libraries/sass/use-if-and-else-to-add-logic-to-your-styles)
1. [Use @for to Create a Sass Loop](https://www.freecodecamp.org/learn/front-end-libraries/sass/use-for-to-create-a-sass-loop)
1. [Use @each to Map Over Items in a List](https://www.freecodecamp.org/learn/front-end-libraries/sass/use-each-to-map-over-items-in-a-list)
1. [Split Your Styles into Smaller Chunks with Partials](https://www.freecodecamp.org/learn/front-end-libraries/sass/split-your-styles-into-smaller-chunks-with-partials)
1. [Extend One Set of CSS Styles to Another Element](https://www.freecodecamp.org/learn/front-end-libraries/sass/extend-one-set-of-css-styles-to-another-element)

## Hands on

Organize your code as shown in the file structure. Divide your CSS into small chunks and import them from a single CSS main file. Remember the importance of the order.
Add mixins to your project and avoid repeating code. Remeber that mixins have a specific file.

## Bonus points

A proffesional guide to read with all the information about Sass: https://sass-guidelin.es

# 04. Advanced HTML

## Pug

As well as in CSS we have Sass, for HTML we have **Pug**.

Clean and organize HTML, that’s what we as Front-end Developers always aim for. Well with Pug, formerly known as “Jade” it’s a high performance and feature-rich templating engine that’s easy to achieve. Simply put, Pug is a clean, white space/indentation sensitive syntax for writing html.

?> Just like SASS, Pug is a prepocessor and, as such it helps you accomplishing tasks like wrapping away repetitive work by providing features not available in plain HTML.

This is how Pug looks like

```pug
doctype html
html(lang='en')
 head
   title Pug
 body
   h1 Pug Examples
   div.container
     p Cool Pug example!
```

will be compiled to

```html
<!DOCTYPE html>
<html lang="en">
 <head>
   <title>Pug</title>
 </head>
 <body>
   <h1>Pug Examples</h1>
   <div class="container">
     <p>Cool Pug example!</p>
   </div>
 </body>
</html>
```

### Text

```pug
     p Cool Pug example!
     p
     | Cool Pug example!
     | This is a long text!
```

### Classes, iDs, attributes

#### Classes

```pug
     div.class-name text
```

```html
    <div class="class-name">text</div>
```

#### ID

```pug
     div#id-name text
```

```html
    <div id="class-name">text</div>
```

#### Attributes

```pug
     img.main-image(src="url/to/image.jpg", alt="Description")
```

```html
    <img src="url/to/image.jpg" alt="Description" />
```

## Pug playground

Pug playground here: https://pug.now.sh/

## Hands on

Convert your code into pug templates and compile it.
