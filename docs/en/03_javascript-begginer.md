# 01. Introduction to Javascript

## Computer programming

Computer programming is a way of giving computers instructions about what they should do next.

These instructions are known as code, and computer programmers write code to solve problems or perform a task.

The end goal is to create something that could mean anything: from a web page, or a piece of software, or even just a pretty picture. That’s why computer programming is often described as a mix between art and science; it’s technical and analytical, yet creative at the same time.

This video explain pretty well the concept of programming:
[![What is Programming?](http://img.youtube.com/vi/FCMxA3m_Imc/0.jpg)](http://www.youtube.com/watch?v=FCMxA3m_Imc "What is Programming?")

[What is Programming?](https://www.youtube.com/watch?v=FCMxA3m_Imc)

## Javascript language

JavaScript is a scripting or programming language that allows you to implement complex things on web pages.

If a website does content update, displays interactive maps, animated 2D/3D, advanced interactions you can bet that JavaScript is probably involved.

- HTML is the markup language that we use to structure and give meaning to our web content, for example defining paragraphs, headings, and data tables, or embedding images and videos in the page.

- CSS is a language of style rules that we use to apply styling to our HTML content, for example setting background colors and fonts, and laying out our content in multiple columns.

- JavaScript is a scripting language that enables you to create dynamically updating content, control multimedia, animate images, and pretty much everything else.

### What can I do with Javascript

This is how Javascript looks like:

```html
<div class="vegetable">I love potato</div>
```

```js
// Save in a constant the an HTML element with the class 'vegetable'
const vegetable = document.querySelector('.vegetable');

// If a user clicks on the HTML element vegetable, we will execute the funcion 'updateVegetableName'
vegetable.addEventListener('click', updateVegetableName);

// The function launches a prompt to ask for a new vegetable name and updates the content of the HTML element with a new text
function updateVegetableName() {
  let vegetableName = prompt('Enter a new vegeatble');
  vegetable.textContent = `I love ${vegetableName}`;
}
```

!> Don't worry if you don't understand this code yet. The most important part is that you understand that using Javascript we can select HTML elements using selectors as we do in CSS and update them.

The core JavaScript language consists of some common programming features that allow you to do things like:

- Store useful values inside variables. In the above example for instance, we ask for a new name to be entered then store that name in a variable called `vegetableName`.

- Operations on pieces of text (known as `strings` in programming). In the above example we take the string `I love` and join it to the `vegetableName` variable to create the complete text label, e.g. 'I love oranges".

- Running code in response to certain events occurring on a web page. We used a `click` event in our example above to detect when the button is clicked and then run the code that updates the text label.

We can do a lot more using Javascript than just updating the DOM and the CSS, we can also use browser geolocation, develop 2D and 3D graphics using WebGL, display video and audio, or connect to external websites or apps and get information using public APIs as retrieving information from twitter or github.

### JavaScript running order

javascript code is executed from top to bottom, in reading order. This is a very common error — you need to be careful that the objects referenced in your code exist before you try to do stuff to them.

## Interpreted versus compiled code

You might hear the terms interpreted and compiled in the context of programming. In interpreted languages, the code is run from top to bottom and the result of running the code is immediately returned. You don't have to transform the code into a different form before the browser runs it.

Compiled languages on the other hand are transformed (compiled) into another form before they are run by the computer. For example, C/C++ are compiled into assembly language that is then run by the computer.

?> JavaScript is an interpreted programming language.

## Server-side versus client-side code

You might also hear the terms server-side and client-side code, especially in the context of web development.

Client-side code is code that is run on the user's computer when a web page is viewed, the page's client-side code is downloaded, then run and displayed by the browser. In this module we are explicitly talking about client-side JavaScript.

Server-side code on the other hand is run on the server, then its results are downloaded and displayed in the browser.

Examples of popular server-side web languages include PHP, Python, Ruby, ASP.NET and... JavaScript! JavaScript can also be used as a server-side language, for example in the popular Node.js environment.

# 02. Developer Tools

Every modern web browser includes a powerful suite of developer tools. These tools do a range of things, from inspecting currently-loaded HTML, CSS and JavaScript to showing which assets the page has requested and how long they took to load.

![devTool](./assets/DevTools.jpg)

## The JavaScript console

The JavaScript console is an incredibly useful tool for debugging JavaScript that isn't working as expected.
It allows you to run lines of JavaScript against the page currently loaded in the browser, and reports the errors encountered as the browser tries to execute your code.

To access the console in any browser

![console](./assets/DevTool-Console.jpg)

Now try entering the following incorrect versions of the code and see what you get.

![error-console](./assets/DevTool-ErrorConsole.jpg)

You'll start to see the kind of errors that the browser returns. Often these errors are fairly cryptic, but it should be pretty simple to figure these problems out!

## Adding JavaScript to your page

### Internal JavaScript

!> **Warning: this method is not recommended**

Open the file in your web browser and in your text editor. You'll see that the HTML creates a simple web.
Next, go to your text editor and add the following in your head — just before your closing `</head>` tag:

```html
<script>
    //Print message in console
    console.log("First way | Internal JavaScript");
</script>
```

### External JavaScript

1. First, create a new file in the same directory as your sample HTML file.
Call it script.js make sure it has that .js filename extension,
as that's how it is recognized as JavaScript.

2. Replace your current `<script>` element with the following:

```html
<script src="script.js" defer></script>
```

3. Inside script.js, add the following script:

```javascript
    //Print message in console
    console.log("Second way | External JavaScript");
```

## Comments in Javascript

As with HTML and CSS, it is possible to write comments into your JavaScript code that will be ignored by the browser, and exist simply to provide instructions to your fellow developers

A single line comment is written after a double forward slash (//), e.g.

```javascript
// I am a comment
```

A multi-line comment is written between the strings /* and */, e.g.

```javascript
/*
  I am a
  multi line
  comment
*/

```

# 03. Javascript tools

## Variables

A variable is a container for a value, like a number we might use in a sum, or a string that we might use as part of a sentence.

Example:

```javascript
const kingGrandson = 'Felipe Juan Froilán de Todos los Santos de Marichalar y Borbón'; //String
const kingGrandsonAge = 20; //Number
const hasTitle = true; //Boolean
const titleName = 'Caballero Divisero Hijodalgo del Ilustre Solar de Tejada'; //String

console.log(kingGrandson + 'has ' + kingGrandsonAge + 'years');
console.log(kingGrandson + 'has a title of' + titleName);
```

### Declaring variables

#### let

!> `var` and `let` mean subtly different things, both having to do with [scope](https://stackoverflow.com/questions/762011/whats-the-difference-between-using-let-and-var-to-declare-a-variable). A good rule of thumb is to use `let` unless you are working with an older version of the JavaScript interpreter.

```javascript
let FIVE = 5;
FIVE = 6;
console.log(FIVE); // 6
```

?> For now, we will use `let` for declaring a variable unless the variable is immutable.

#### const

You can declare a constant with the `const` operator. Constants are like variables declared with `let`, but cannot change their value through reassignment.

```javascript
const FIVE = 5;
FIVE = 6;  // TypeError: Assignment to constant variable.
```

!> **Note** that each line of JavaScript code ends with the `;`. This is optional for the code to work (sometimes, and the rules are inconsistent) but **not** optional when taking into consideration style guidelines.

### Undefined and value

Once you've declared a variable, you can initialize it with a value.

```javascript
const FIVE = 5;
console.log(FIVE); // 5
```

Otherwise, the variable does not exist and we cannot use it

```javascript
console.log(FIVE); //ReferenceError: FIVE is not defined.
```

We can also declare an empty variable

```javascript
const FIVE;
console.log(FIVE); //undefined
```

### Variable Naming

A safe convention to stick to is so-called "lower camel case", where you stick together multiple words, using lower case for the whole first word and then capitalize subsequent words. We've been using this for our variable names in the article so far.

Variables are case sensitive — so `myage` is a different variable to `myAge`.

Constants can be written in all uppercase

```javascript
const KINGNAME = 'Felipe Juan Froilán';
let kingAge = 20;
let kingStudies = 'ADE';
```

## Conditionals

Conditional statements allow us to represent decision making in JavaScript, from the choice that must be made (e.g. "one cookie or two"), to the resulting outcome of those choices.

The most common type of conditional statement is the `if...else`:

```javascript
const isKing = false;

if (isKing === true) {
  // code to run if condition is true
  console.log('¡Viva el rey!');
} else {
  // run some other code instead
  console.log('¡Guillotina!');
}
```

If there is more than one option:

```javascript
const isKing = 'Felipe';

if (isKing === 'JuanCar') {
  console.log('¡Este es el rey anterior!');
} else if (isKing === 'Felipe') {
  console.log('¡Este es el rey de ahora!');
} else {
  console.log('¡Viva la república!');
}
```

### Operators

- `===` means equal
- `!==` means not equal
- `<` or `>` test if one value is less than or greater than another.
- `<=` or `>=` test if one value is less than or  or equal to, greater than  or equal to.

### Multiple conditionals

You can have more than one condition

```javascript
const isKing = true;
const kingAge = 86;

if (isKing && kingAge > 46) {
  console.log('¡El rey viejo!');
} else {
  // run some other code instead
  console.log('¡El rey de ahora!');
}
```

- `&&` means AND
- `||` means OR

## Arrays

Arrays are lists of values tha can be stored in variables and dealt with in much the same way as any other type of value, the difference being that we can access each value inside the list individually, and do super useful and efficient things with the list, like loop through it and do the same thing to every value.

Imagine we want to save a list of every item a consumer bought and print them out in an invoice. For example, if we didn't have arrays, we'd have to store every item in a separate variable and print each item separately. If we had 10 items to add to the invoice it would already be annoying, but what about 100 items, or 1000? We'll return to this example later on in the article.

```javascript
const product1 = 'Toilet paper';
const product2 = 'Scissors';
const product3 = 'Tomatoes';
const product4 = 'Towels';
const product5 = 'Shoes';

// And so os with every product
// Instead

const productList = ['Toilet paper', 'Scissors', 'Tomatoes', 'Towels', 'Shoes'];
```

An array can sabe multiple values:

```javascript
var random = ['tree', 795, [0, 1, 2]];
```

### Accessing arrays

You can then access individual items in the array using bracket notation.

```javascript
const productList = ['Toilet paper', 'Scissors', 'Tomatos', 'Towels', 'Shoes'];

console.log(productList[0]); // 'Toilet paper'
```

### Looping arrays

If we would like to loop an array to display all the values in it, we should use a loop.

```javascript
const productList = ['Toilet paper', 'Scissors', 'Tomatos', 'Towels', 'Shoes'];

productList.forEach((product, index) => {
    console.log(index, product); // index
});
```

## Functions

A function is a code snippet that can be called by other code or by itself, or a variable that refers to the function.

Imagine a machine, each time you push a button it does something. You don't need to know how it works, the machine just get some material, transforms it, and returns something modified. If you open it, you can understand how it transforms it.

```javascript
function random() {
  return Math.floor(Math.random());
};

//or

const random = () => {
   return Math.floor(Math.random());
};
```

Sometimes, you can add something to the machine and it converts it and returns something else:

```javascript
function add(number1, number2) {
  return number + number;
}

// or

const add = (number1, number2) => {
   return number + number;
};
```

To activate it, you should **push the button**

```javascript
random();
add(2, 3);
```

## Hands on!

### Exercise 1 - The Lifetime Supply Calculator

How many potatoes will a person eat until the end of his life? Discover yourself!

 1. Store the persons current age into a variable.
 1. Store an stimated maximum age into a variable.
 1. Store an estimated amount per week (as a number).
 1. Calculate how many weeks will happen until the end of this person life.
 1. Calculate how many potatoes would eat total for the rest of his life.
 1. Output the result to the screen by console like so: "NAME has NN years and will eat NN potatoes until age of X".

### Exercise 2 - True or false

Using promp, variables and **conditionals**, ask questions to the users and display the result on the console.

  1. Ask: "Tomatos are fruits, not vegetables: true or false". If that answer is "true" you show "correct", otherwise show "incorrect".
  1. Ask: "You should drink 8 glasses of water: true or false". If that answer is "false" you show "correct", otherwise show "incorrect".
  1. Ask: "Fishes have only three seconds of memory: true or false". If that answer is "false" you show "correct", otherwise show "incorrect".
  1. Ask: "The Great Wall of China is the only man made structure visible from space
The Great Wall of China: true or false". If that answer is "true" you show "correct", otherwise show "incorrect".

Create more true or false questions.

#### Bonus points

1. Create a variable `points` and initialize it to zero.
2. If the answer is correct, add 10 points to the `points` variable.
3. If the answer is incorrect, remove 5 points to the `points` variable.
4. Display how many points the user has on the console.

### Exercise 3 - A dinner

Imagine you are a famous singer in a band and you want to invite other musicians to a dinner.

Write an array of every musician and its band in a format `musician:band` and using only one console log, display the list of assistants in the console.

# 04. Events and the DOM

## The Document Object Model (DOM)

The Document Object Model (DOM) is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style, and content. The DOM represents the document as nodes and objects.

The DOM is an object-oriented representation of the web page, which can be modified with a scripting language such as JavaScript.

When you create a script–whether it's inline in a `<script>` element or included in the web page by means of a script loading instruction–you can immediately begin using the API for the document or window elements to manipulate the document itself or to get at the children of that document, which are the various elements in the web page.

```javascript
let paragraphs = document.getElementsByTagName("P");
```

### Dom Interfaces

The following is a brief list of common APIs in web and XML page scripting using the DOM.

### Document.getElementById(id)

The Document method getElementById() returns an Element object representing the element whose id property matches the specified string.

```javascript
const element = document.getElementById('unique-element');
```

### Document.getElementsByTagName(tagname)

The Element.getElementsByTagName() method returns a live HTMLCollection of elements with the given tag name.

```javascript
const element = document.getElementsByTagName('main');
```

### EventTarget.addEventListener()

The EventTarget method `addEventListener()` sets up a function that will be called whenever the specified event is delivered to the target.

```javascript
const el = document.getElementById("outside");
el.addEventListener("click", getOutside, false);
```

### Element.innerHTML

The Element property `innerHTML` gets or sets the HTML or XML markup contained within the element.

```javascript
const name = "John";
const el = document.getElementById("outside");
el.innerHTML = name; // harmless in this case
```

### Document.createElement()

In an HTML document, the document.createElement() method creates the HTML element specified by tagName

```javascript
const newDiv = document.createElement("div");
```

### Node.appendChild()

The Node.appendChild() method adds a node to the end of the list of children of a specified parent node.

```javascript
const el = document.getElementById("outside");
const newDiv = document.createElement("div");
el.appendChild(newDiv);
```

## Event listeners

There are 3 ways to register event handlers for a DOM element.

### EventTarget.addEventListener()

The EventTarget method `addEventListener()` sets up a function that will be called whenever the specified event is delivered to the target.

```javascript
const myButton = document.querySelector('#my-button');

myButton.addEventListener('click', greet);

const greet = (event) => {
    console.log('greet');
    alert('hello world');
}
```

This is the method you should use in modern web pages.

!> Avoid: HTML attribute `onclick`

```javascript
<button onclick="alert('Hello world!')">
```

!> Avoid: Element property `onclick`

```javascript
myButton.onclick = function(event){alert('Hello world');};
```

## Event Interface

Event handlers may be attached to DOM elements (as a `button`), the document, the Window...etc.

When an event occurs as we have seen before, a new `Event` object is created through the event listeners.

Let's check how the Event Object looks like:

```javascript
const myButton = document.querySelector('#my-button');

const print = (event) => {
    console.log('print:', event);
    alert('hello world');
}

myButton.addEventListener('click', print);
```

The Event interface is used to provide contextual information about an event to the handler processing the event.

![./assets/event.png](Event Object example)

### event.target

The target property of the Event interface is a reference to the object that dispatched the event.

For instance, this is a good example of use case. We want to know which element has been clicked to append a class and change the style

```javascript
// Create an unordered list
const ul = document.createElement('ul');
document.body.appendChild(ul);

// Create two list items and append it to the list
const li1 = document.createElement('li');
const li2 = document.createElement('li');
li1.textContent = 'Example1'
li2.textContent = 'Example2'
ul.appendChild(li1);
ul.appendChild(li2);

// Set a function that adds a class to highlight the item
const highlight = (event) => {
    console.log(event.target);
    event.target.classList.add('highlight');
}

// Attach the listener to the list
// It will fire when each <li> is clicked
const listItem = document.querySelector('ul');
listItem.addEventListener('click', highlight);
```

```css
.hightlight {
    color: red;
}
```

![Simple event target on Codepen](https://codepen.io/Xaviju/pen/ydzvEd)

### event.currentTarget

Similar to the previous one, except that in this case the event log will display the element that creates the event listener instead of the clicked element.

Using `currentTarget`, the log would be the `ul` instead of the `li`.

Try updating the value on the previous example and see what happens

### preventDefault()

This method tells the browser that if the event does not get explicitly handled, its default action should not be taken as it normally would be.

For instance, if we add an event listener to a click on an checkbox in a form and we set the `preventDefault` the expected behaviour on a checkbox (being clicked) won't happen

Example: [Blocking default click handling](https://codepen.io/Xaviju/pen/MMEVya?&editable=true)

## AddEventListener

`addEventListener()` sets up a function that will be called whenever the specified event is delivered to the target.

This functions receives at least parameters:

- **Type** The event type: click, focus, blur, submit, keydown...(*)
- **listener** The function that will receive the event object.

```javascript
myButton.addEventListener(type, listener);
```

?> [Event reference](https://developer.mozilla.org/en-US/docs/Web/Events)

## Hands on

Crea un juego para que un usuario tenga que adivinar un número entre cero y 100:

- El usuario tiene que introducir un número a través de un input y enviarlo a través de un botón.
- Tenemos que avisarle cada vez que pulse el botón de enviar de si el número es correcto y si no, comprobar si se ha pasado por arriba o por abajo y avisarle.
- Si sobrepasa los 10 intentos le avisamos que ha perdido e iniciamos el juego otra vez

Cómo hacerlo:

1. Crea el HTML necesario: input, botón, número de vidas...etc.
2. Crea los estilos básicos para que se vea bien
3. Crea una variable que te de un número al azar entre cero y 100
4. Crea una variable que registre los intentos que ha hecho el usuario. Al principio vale cero
5. Registra el click en el botón
6. Crea una función que compruebe si el número que ha introducido el usuario es igual al númbero al azar.
    1.1 Si es igual: felicita al usuario visualmente y reinicia el contador de intentos a cero y crea otro número al azard
    2.2 Si es mayor: Avisa al usuario que se ha pasado, restale una vida y continúa.
    3.3 Si es menor: Avisa al usuario que se ha ido por arriba, restale una vida y continúa.
7. Si el usuario llega a 10 intentos, avísale que ha perdido y reinicia todos los valores.
