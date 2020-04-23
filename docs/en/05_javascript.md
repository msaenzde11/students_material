
# 01. Arrays in depth

So far we've covered how to **loop** over iterable elements in javascript, such as arrays.

?> **Disclaimer**: objects are [also iterable](https://alligator.io/js/for-of-for-in-loops/#forin) but let's leave that for another time.

We should know by now how to use a `for` loop and call the `.forEach` function within an array without much struggle.

These forms of iterating over arrays and manipulating them are ok in most cases, and you could easily do pretty much everything you need with those two types of loops, but there's another way with which you can save a lot of code while keeping your codebase clean and [avoid mutating your arrays](https://www.freecodecamp.org/news/an-introduction-to-the-basic-principles-of-functional-programming-a2c2a15c84/) (more on this later).

Javascript lets us do three basic operations with three different methods that we're going to teach you right now. These three functions have all one thing in common, and that is that they are [Higher order functions](https://www.freecodecamp.org/news/a-quick-intro-to-higher-order-functions-in-javascript-1a014f89c6b/). Don't worry if you don't understand that concept now, just remember that all three work exactly the same: They are **functions** that accept another function as their parameter (or **[callback function](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)**).

Let's see them in action!

## Map

According to the [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) documentation, the map function:

> "**creates a new array** with the results of calling a provided function on every element in the calling array".

This is pretty much what we were doing with our arrays, right? The main difference is that `map` already returns a new array (which you normally **store** somewhere, of course) with the result of **executing our callback function** once for each one of the elements of our array. So let's see it in action:

```js
const arr = [1, 2, 3, 4, 5, 6, 7];
const multiplyBy2 = n => n * 2;

const arrTimes2 = arr.map(multiplyBy2);

console.log(arrTimes2); // [2, 4, 6, 8, 10, 12, 14]
```

Ok, so let's dive first into that code from above:

1. First, we've **declared** an array with some numbers, from 1 to 7.

2. Then, we've **declared a new function** that **receives** a number and multiplies it by 2, **[returning](https://jaketrent.com/post/javascript-arrow-function-return-rules/)** the result.

3. We call the `map` function from our array, executing our previously declared function with the element provided by `map`, as many times as elements has the array.

Note that the following code would do exactly the same:

```js
const arr = [1, 2, 3, 4, 5, 6, 7];

const arrTimes2 = arr.map(n => n * 2);

console.log(arrTimes2); // [2, 4, 6, 8, 10, 12, 14]
```

Easy, right? Certainly it saves us a lot of code considering how we would have done it before:

```js
const arr = [1, 2, 3, 4, 5, 6, 7];
const arrTimes2 = [];
const multiplyBy2 = n => n * 2;

for (let i = 0; i < arr.length; i++) {
    const result = multiplyBy2(arr[i]);
    arrTimes2.push(result);
}

console.log(arrTimes2); // [2, 4, 6, 8, 10, 12, 14]
```

Now, let's move to the next function that will let us easily work with our arrays.

## Filter

As its own name tells us, filter is used to select certain elements of an array and choose them to be part of a new array, based on a certain condition. The filter function allows us to discard elements that we don't need in our newly created array. According to [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter):

?> The filter() method creates a new array with all elements that pass the test implemented by the provided function.

As `map` does, `filter` also returns a different array than the one we are working with, with the exception that it will contain only the elements that the **returning expression** of our callback function returns `true` for.

Let's see it better with an example:

```js
// Let's return those words longer than 6 characters
const words = ['Hello', 'Javascript', 'Web development', 'CSS', 'HTML'];

const longWords = words.filter(word => {
    return word.length > 6;
});

console.log(longWords); // ['Javascript', 'Web development']
```

As you can see, filter is pretty straighforward. You just need to return an expression that evaluates to `true` or `false`, and all the elements of the array that pass that test, will be in the new array. All those that don't pass it, will be automatically discarded.

Again, this saves us from doing a lot of unnecessary extra steps as we needed to do before:

```js
// Let's return those words longer than 6 characters
const words = ['Hello', 'Javascript', 'Web development', 'CSS', 'HTML'];
const longWords = [];

for (let i = 0; i < words.length; i++) {
    if (words[i].length > 6) {
        longWords.push(words[i]);
    }
}

console.log(longWords); // ['Javascript', 'Web development']
```

Now let's see the last method that will make our lives easier when working with arrays.

## Reduce

The `Reduce` function works pretty much the same as the other two. It accepts a function as a parameter exactly the same way as `map` and `filter` do, with the exception that this callback function (called reducer), instead of receiving the current element of the array as first argument, takes the accumulated result (accumulator) of the previously executed iterations. Let's see how [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce) defines this method and then we'll see it with some code:

?> The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.

Another thing to notice is that instead of returning a new array, `reduce` always outputs a single value, the result of accumulating the returning value of each iteration. Let's see how it works:

```js
// Let's get the sum of all the values in the array
const nums = [124, 22, 874, 173, 5739];

const sumOfNums = nums.reduce((accum, num) => {
    return accum + num;
}, 0);

console.log(sumOfNums); // 6932
```

As we said before, you can notice how on each iteration, we receive the previous result of adding the accumulator to the element of the array, resulting in the end with the ouput of the sum of all the elements in the array.

There's a second thing to take into account with the `reduce` function, and that is that apart from the accumulated value and the reducer function, we can pass a third parameter, consisting of the initial value that our reducer function will accept as accumulator on the first iteration. Let's see it better with an example:

```js
// Let's get the multiplication of all the values in the array
const nums = [124, 22, 874, 173, 5739];
const multiplicationOfNums = nums.reduce((accum, num) => {
    // On the first iteration, when num's value is 124
    // accum's value will be 1
    return accum * num;
}, 1 /* what if this were a zero? */);
console.log(multiplicationOfNums); // 2367217302384

```


This might seem confusing at first, but everything will be crystal clear once you start practicing with a few exercises! 💻

# Exercises

## 1. Map exercises

- Given the following array, create a second array with the result of getting the power of each number by itself.

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Write your code here!

// Expected result
// [1, 4, 27, 256, 3125, 46656, 823543, 16777216, 387420489, 10000000000]
```

- Given the following array, create a second array that uses each one of the words to form the sentences seen below.

```js
const foodList = ['Pizza', 'Ramen', 'Paella', 'Chuletón'];

// Write your code here!

//Expected result:
/* [
    'Since I'm Italian, I love eating Pizza',
    'Since I'm Japanese, I love eating Ramen',
    'Since I'm from Valencia, I love eating Paella',
    'Although I don't eat meat, Chuletón is certainly tasty'
   ]
*/
```

- Given the following array, create a second array that forms sentences using the objects' properties:

```js
const mfrStaff = [
  {
    name: 'Andrea',
    role: 'coordinator',
    hobbies: ['sing', 'watch movies']
  },
  {
    name: 'Xavi',
    role: 'teacher',
    hobbies: ['read', 'code']
  },
  {
    name: 'Ricardo',
    role: 'teacher',
    hobbies: ['read', 'garden']
  },
  {
    name: 'Rafa',
    role: 'teacher',
    hobbies: ['travel', 'watch series']
  },
  {
    name: 'Jordi',
    role: 'teacher',
    hobbies: ['travel', 'build robots']
  }
];

// Write your code here!

// Expected result
/*
  [
    'Andrea is a coordinator and they like to sing and watch movies',
    'Xavi is a teacher and they like to read and code',
    'Ricardo is a teacher and they like to read and garden',
    'Rafa is a teacher and they like to travel and watch series',
    'Jordi is a teacher and they like to travel and build robots'
  ]
*/
```

## 2. Filter exercises

- Given the following array, create a second array only with the even numbers

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Write your code here!

// Expected result
// [2, 4, 6, 8, 10]
```

- Given the following array, create a second array that filters out all the food that has meat and outputs the sentence seen below

```js
// Tip: You can chain map and filter to first remove the elements you don't want in your new array and then giving them the desired shape

const foodList = [
  {
    name: 'Tempeh',
    isVeggie: true
  },
  {
    name: 'Cheesbacon burguer',
    isVeggie: false
  },
  {
    name: 'Beyond meat burguer',
    isVeggie: true
  },
  {
    name: 'Chuletón',
    isVeggie: false
  }
];

// Write your code here!

//Expected result:
/* [
    'Nothing like a good Tempeh for dinner!',
    'Nothing like a good Beyond meat burguer for dinner!'
   ]
*/
```

- Given the following array, create a second array that **outputs only the name** of the products that cost less than 200€

```js

const inventory = [
  {
    name: 'Mobile phone',
    price: 199
  },
  {
    name: 'TV 4K',
    price: 400
  },
  {
    name: 'PS5',
    price: 600
  },
  {
    name: 'Programming course license',
    price: 155
  }
];

// Write your code here!

// Expected result
/*
  [
    'Mobile phone',
    'Programming course license'
  ]
*/
```

## 3. Reduce exercises

- Given the following array, get the multiplication of all the elements of it.

```js
const numbersList = [45, 5, 1, 23, 32];

// Write your code here!

// Expected output --> 165600
```

- Given the following array, concatenate all the elements in the array using `.reduce()`.

```js
const sentenceElements = [
  'My',
  'name',
  'is',
  /* Place your name here */,
  'and',
  'I',
  'love',
  'javascript'
];

// Write your code here!

// Expected result --> 'My name is John Doe and I love javascript'
```

- Given the following array, get the total amount of those products that belong to the category of `coding`

```js
const booksList = [
  {
    name: 'You don\'t know JS',
    author: 'Kyle Sympson',
    price: 15,
    category: 'code'
  },
  {
    name: 'The handmaids tale',
    author: 'Margaret Atwood',
    price: 18,
    category: 'novel'
  },
  {
    name: 'Game of Thrones',
    author: 'George R. Martin',
    price: 32,
    category: 'Fantasy'
  },
  {
    name: 'Eloquent Javascript',
    author: 'Marijn Haverbeke',
    price: 40,
    category: 'code'
  }
];

// Write your code here!

// Expected result --> 55
```

## Exercises on FreeCodeCamp

!> These exercises are required to complete MFR coding project. Please login into your FreeCodeCamp profile to save the advance. If you have any problems, contact the teachers in [Slack](mfrcodingproject.slack.com).

1. [Use the map Method to Extract Data from an Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-the-map-method-to-extract-data-from-an-array)
1. [Seek and Destroy](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/intermediate-algorithm-scripting/seek-and-destroy)
1. [Sum All Numbers in a Range](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/intermediate-algorithm-scripting/sum-all-numbers-in-a-range)
1. [Use Higher-Order Functions map, filter, or reduce to Solve a Complex Problem](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-higher-order-functions-map-filter-or-reduce-to-solve-a-complex-problem)

# 02. Functions in depth

A good programming language is more that just a mean for instructing a computer to perform tasks. It also help us think about the processes, by providing a way to **combine simple ideas to form more complex ones**.

Abstractions allow to write bigger pieces of code in terms of simpler elements. This is similar to a natural language, where we define new terms so we can refer to them later without giving all the details
again. JavaScript has two means by which compound elements can be named and manipulated as units: **functions** and **objects**.

Functions are descriptions of the rules for manipulating data. They create abstractions around procedures, that is, a series of steps that we want to make on some given elements to produce a result. They take arguments and return a value, in a way similar to functions in
mathematics.

In JavaScript, functions are first-class citizens, that is, they can be passed as arguments to other functions, and be returned from functions. Thus, in the same way than a variable can have a number or
a string as a value, it can also have a function, and we can manipulate them in similar ways. This feature gives us a very powerful tool to write good, readable code.

## Syntax

Let's see again an example of a function:

```js
function average(x, y) {
    let sum = x + y;
    return sum / 2;
}
```

The reserved word `function` says that what comes next is the name of a function (`average` in this case). Then come the **arguments** (sometimes also called **parameters**) of the function (`x` and `y`),
and finally the **body**, which is enclosed in brackets. The **result** will be the value that appears after `return`.

A function is called by writing the name of the function and then passing it some parameters in parenthesis. For example:

```js
let x = 8, y = 10;

let z = average(x, y);

console.log(`The average of ${x} and ${y} is ${z}.`);
```

### Arrow functions

A function can also be defined in a different way. Instead of using the word `function`, we can simply put a "fat arrow" `=>` that goes from the arguments to the value of the function.

```js
const average = (x, y) => {
    let sum = x + y;
    return sum / 2;
};
```

If there is only one argument to the function, the parenthesis can be omitted:

```js
const double = x => {
    return 2 * x;
};
```

Also, instead of writing a block of code, we put a single **expression** which will be the returned value. So, the above code is equivalent to:

```js
const double = x => 2 * x;
```

?> This notation is particularly useful when we want to pass a small function to other functions, such as `map`, `filter` and `reduce` that we saw previously.

## Scope

The variables defined inside the functions exist only within its body, as it is delimited by the block:

```js
let x = 3;
function f() {
    let x = 4; // different x!
    console.log(x); // outputs 4
}
console.log(x); // outputs 3
```

They are called *local variables* because they reference values only inside the block in which they are declared. If there is already a variable with the same name, they *override* it within the scope where they are declared.

## Default values

An argument can be given a default value, which will be used only if we call the function without passing that argument.

For example:

```js
function multiply(a, b = 3) {
    return a * b;
}

multiply(5, 2); // returns 10

multiply(5); // returns 15
```

?> Actually, all arguments are always given a default value, which is `undefined`, unless a different default value is given in the definition of the function. In particular, this means that a function can always be called with less arguments than appear in the definition (sometimes the functions then just check if they are `=== undefined` and change their behavior depending on that). We don't recommend writing code in such a way.

### Variadic functions

We can define a function to take an arbitrary number of arguments, and access all of them by using the rest parameter syntax.

For example:

```js
function sum(...args) {
    let x = 0;

    for (let i = 0; i < args.length; i++)
        x += args[i];

    return x;
}

sum(1, 2); // returns 3
sum(1, 2, 3); // returns 6
```

A function's last parameter can be prefixed with `...` and it will make the remaining given arguments to be placed in an array.

```js
function myFun(a, b, ...manyMoreArgs) {
  console.log("a", a);
  console.log("b", b);
  console.log("manyMoreArgs", manyMoreArgs);
}

myFun("one", "two", "three", "four", "five", "six");

// Outputs:
// a, one
// b, two
// manyMoreArgs, [three, four, five, six]
```

Another way is to use the reserved keyword `arguments`. This keyword will have a list of the values of all the arguments:

```js
function sum() {
    let x = 0;

    for (let i = 0; i < arguments.length; i++)
        x += arguments[i];

    return x;
}
```

## Recursive functions

Functions can call themselves as part of their computation. For example, the following function computes the value of the factorial of a number (`n! = n * (n - 1) * (n - 2) * ... * 1`):

```js
function factorial(n) {
    if (n === 0)
        return 1;

    return n * factorial(n - 1);
}

factorial(3); // returns 6
```

This function uses the fact that `factorial(n) = n * factorial(n - 1)`. It works because at some point we will reach the call to `factorial(0)`, which is 1, and from there the rest of the values can be computed.

?> Recursive calls can be very useful, especially when we have processes that traverse certain data structures such as *trees*.

## Closures

A function can capture its non-local variables by reference.

```js
function counter() {
    let count = 0;

    return () => {
        count += 1;
        return count;
    };
}

let closure = counter();

closure(); // returns 1
closure(); // returns 2
closure(); // returns 3
```

In this example, the function `counter` takes no arguments and returns a function (we can do that, since functions are first-class citizens in JavaScript!). The returned function, when called without arguments, will increase the value of `count`, which is not visible from outside the function, but has been "captured" by the function and can use it. The `count` variable is not free anymore, and we have formed what we call a *closure*.

## Exercises on FreeCodeCamp

!> These exercises are required to complete MFR coding project. Please login into your FreeCodeCamp profile to save the advance. If you have any problems, contact the teachers in [Slack](mfrcodingproject.slack.com).

1. [Use Arrow Functions to Write Concise Anonymous Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-arrow-functions-to-write-concise-anonymous-functions)
1. [Write Arrow Functions with Parameters](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/write-arrow-functions-with-parameters)
1. [Global Scope and Functions](https://www.freeCodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-scope-and-functions)
1. [Local Scope and Functions](https://www.freeCodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/local-scope-and-functions)
1. [Global vs. Local Scope in Functions](freeCodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-vs.-local-scope-in-functions)

# 03. Objects in depth

In the same way that functions abstract processes, objects abstract data. Objects can contain many values, and they are written as `property: value` pairs.

Let's see again how to define a simple object:

```js
const p = {
    firstName: 'Ned',
    lastName: 'Stark',
    age: 40,
    isActive: true
};
```

?> To access a property of an object we can use `p.name` or `p['firstName']`. We can also loop over the properties with `for (x in p) { ... }`.

We already saw objects in the course. Now we are going to see some more advanced material related to them.

## This

Objects can contain any kind of values, and in particular they can contain functions. The functions defined inside an object are normally called *object methods*.

Let's try to create a method that returns the full name:

```js
const p = {
    firstName: 'Ned',
    lastName: 'Stark',
    fullName: function() { return this.firstName + ' ' + this.lastName; },
    age: 40,
    isActive: true
};
```

By using `this` we are able to make the function defined inside the object to refer to other properties of the object.

## Constructor

If we are going to create many objects with a similar structure, we can define an *object type*. For example, suppose you want to create an object type for cars. You want this type of object to be called Car, and you want it to have properties for make, model, and year. To do this, you would write the following function:

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
```

Notice the use of `this` to assign values to the object's properties based on the values passed to the function.

Now you can create an object called mycar as follows:

```js
var mycar = new Car('Eagle', 'Talon TSi', 1993);
```

This statement creates `mycar` and assigns it the specified values for its properties. Then the value of `mycar.make` is the string `"Eagle"`, `mycar.year` is the integer 1993, and so on.

You can create any number of Car objects by calls to new. For example,

```js
var kenscar = new Car('Nissan', '300ZX', 1992);
var vpgscar = new Car('Mazda', 'Miata', 1990);
```

>? (The examples come from this [MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects).)

## Spread syntax

We can use the so-called *spread syntax* (`...`) for various purposes.

?> You can find a detailed reference in [MDN-Spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax), but we will mention briefly the different uses here.

### Destructuring

For function calls:

```js
myFunction(...iterableObj);
```

For array literals or strings:

```js
[...iterableObj, '4', 'five', 6];
```

For object literals:

```js
let objClone = { ...obj };
```

?> More details in
[MDN-Destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).

### Assignment

```js
[a, b] = [10, 20];

console.log(a);  // 10
console.log(b);  // 20

[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest);  // [30, 40, 50]
```

## Exercises on FreeCodeCamp

!> These exercises are required to complete MFR coding project. Please login into your FreeCodeCamp profile to save the advance. If you have any problems, contact the teachers in [Slack](mfrcodingproject.slack.com).

1. [Create a Basic JavaScript Object](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/create-a-basic-javascript-object)
1. [Use Dot Notation to Access the Properties of an Object](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/use-dot-notation-to-access-the-properties-of-an-object)
1. [Make Code More Reusable with the this Keyword](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/make-code-more-reusable-with-the-this-keyword)
1. [Define a Constructor Function](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/define-a-constructor-function)
1. [Use a Constructor to Create Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/use-a-constructor-to-create-objects)
1. [Understand the Constructor Property](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/understand-the-constructor-property)
1. [Use Closure to Protect Properties Within an Object from Being Modified Externally](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/use-closure-to-protect-properties-within-an-object-from-being-modified-externally)
1. [Use the Rest Parameter with Function Parameters](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-the-rest-parameter-with-function-parameters)
1. [Use the Spread Operator to Evaluate Arrays In-Place](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-the-spread-operator-to-evaluate-arrays-in-place)
1. [Use Destructuring Assignment to Extract Values from Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-to-extract-values-from-objects)
1. [Use Destructuring Assignment to Assign Variables from Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-to-assign-variables-from-objects)
1. [Use Destructuring Assignment to Assign Variables from Arrays](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-to-assign-variables-from-arrays)

# 04. API Calls

We can retrieve information that is not already present in our JavaScript program by means of making an *external call*, that is, sending a request to a remote server and then retrieving the answer
from inside our program.

To make the request we need to convert the data we send into a string. Also, to understand the response, which will be a text, we need to convert it into objects in JavaScript. The process to convert the data from/to text form is called *serialization*. The format we will use is [JSON](https://en.wikipedia.org/wiki/JSON).

When we make remote requests, the responses can take a long time to reach the client again. We don't want our program to freeze and stop responding, so the way we handle this communication is *asynchronously*. There are different ways to execute code asynchronously, but we will see only the more modern one, which is based on the [fetch method](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch). This will return a special kind of object, which is called a
[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise).

## JSON

To convert some data into a JSON string, we use the `JSON.stringify` function:

```js
const data = ...;

const s = JSON.stringify(data);
```

Conversely, we can recover the data from its serialized form with `JSON.parse`:

```js
const data = JSON.parse(s);
```

## Promises

A [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) is a special kind of object, which is created with a callback function which will act on the data once it is retrieved from the server.

```js
var promise1 = new Promise(function(resolve, reject) {
    setTimeout(function() {
        resolve('foo');
    }, 300);
});

promise1.then(function(value) {
    console.log(value);  // outputs "foo"
});

console.log(promise1);  // outputs [object Promise]
```

## Old days

The original In the old days, the only way to retrieve content from a
server was by means of a `XMLHttpRequest`. The way they were done
looked like this:

```js
var request = new XMLHttpRequest();

request.open('GET', 'https://ghibliapi.herokuapp.com/films', true);
request.onload = function() {
    // Begin accessing JSON data here
    var data = JSON.parse(this.response);

    if (request.status >= 200 && request.status < 400) {
        for (var i = 0; i < data.length; i++)
            console.log(data[i].title);
    } else {
        console.log('error');
    }
}

request.send();
```

(By the way, see the funny use of `var` and `for (var i ...`?  This
looks indeed like old JavaScript. Nowadays we would use `const` and
`data.forEach(film => console.log(film.title))` instead.)

## Exercise 1 | Random number

Let's play a little with the codepen code of the previous example. Looking at the documentation of 'rand.fun', we will ask for an integer (integer).

Can we play by adding parameters to the URL of the key type = value, always after character? and separated by &, for example if you wanted to request a string with a certain length, the url would look like this

[https://api.rand.fun/text/password?length=20](https://api.rand.fun/text/password?length=20)

### Random Dog | Complete example of a fetch request

Display a random dog picture requesting the image to an external server.

Expected result: [Codepen Example](https://codepen.io/adalab/pen/oqQNvK?editors=1010)

Solution:

```javascript

fetch('https://dog.ceo/api/breeds/image/random')
  .then(response => response.json())
  .then(data => {
    const img = document.querySelector('img');
    img.src = data.message;
    img.alt = 'Un perro';
  });

```

## Exercise 2 | Chihuahuas, Chihuahuas everywhere

Let's keep playing with the [Dog API](https://dog.ceo/dog-api/):

a) Modify the previous example so that the photos of our page only appear dogs of the Chihuahua breed.

b)  Encapsulate all the logic to create a request in a function. Add a button with the text 'Show me another Chihuahua' so that when pressed, another request is made to the server of a random image and a new image of Chihuahua appears.

## Exercise 3 | Github User

Let's explore a new API: [the GitHub user API](https://developer.github.com/v3/users/).

The URL of this API is `https://api.github.com/users/{username}`, where `{username}` is the name of the user on GitHub. For example, here is the URL to obtain Isra user information `https://api.github.com/users/mfrcodingproject`. If you put this URL in a new browser tab you can see what data the API returns.
We are going to create a page with a text input and a search button. The user will enter a GitHub username in the input. We will prepare a function that will be executed when the search button is pressed and that contains a request to the API to obtain information from that user and thus display it on our page:

- first name
- number of repositories
- avatar (image)

## Exercise 4 | Github User no Found

Now, use the .catch for show a message when doesn't exist the user.

[Catch documentation](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

Cacth Example:

```javascript
fetch('https://jsonplaceholder.typicode.com/404')
  .then(res => {
    if(res.ok) {
      return res.json();
    } else {
      throw Error(`Request rejected with status ${res.status}`);
    }
  })
  .catch(console.error)
```

## Exercise 5 | Github Repository list

List the repos of an organization in Github

Let's continue exploring the GitHub API by exploring the part of the API to access the information about organizations. The URL of this API is `https://api.github.com/orgs/${orgname}/repos`, where {orgname} is the name of the organization on GitHub. For example, here you have the URL to obtain information from the Adalab organization `https://api.github.com/orgs/mfrcodingproject`. If you put this URL in a new browser tab you can see what data the API returns.

The objective of this exercise is to display on a website the complete list of repositories of an organization that are created in GitHub.

## Exercise 6 | Method post

This is a fetch with post method.

!> This api is fake. But in the real world this method save information.

When we send information with post we use body for send information by secure way.
And we use the header for send information about the information how the format **'application/json'**.

``` javascript
 const myPost = {
        title: 'A post about true facts',
        body: 'Once upon a time.....',
        userId: 8888888887
    };

    fetch('https://jsonplaceholder.typicode.com/posts', {
        method: 'POST',
        body: JSON.stringify(myPost),
        headers: {
            'Content-Type': 'application/json'
        }
    })
    .then(response => response.json())
    .then(data => {
        console.log("---------- we save our information -----------")
    });

    fetch(`https://jsonplaceholder.typicode.com/post/${myPost.userId}`)
        .then(response => response.json())
        .then(data => {
            console.log("---------- we recover our information -----------");
            console.log(data);
        });
```

## Exercise 7 | Extra Exercise, Real Example

Firebase is one platform where we can host static web page and little json data base and more.

Now we'll use firebase a json database for save our own information.

- First step. We go to `https://firebase.google.com`.
And we create a free count. We can entry with a google count.

- Second step. In the console we'll create a new proyect.
When we ask by google analytics we click "now no".

![firebase1](./assets/firebase1.jpg)

![firebase2](./assets/firebase2.jpg)

Now we have a proyect in firebase.

![firebase3](./assets/firebase3.jpg)

- Third step. We go to Develoment -> Database and we create a Database.

![firebase4](./assets/firebase4.jpg)

- Fourth step. we selecte block mode. Only can read but only you can write,

![firebase4](./assets/firebase5.jpg)

- Fifth step. Create a file with name users.json and add the next data.

```json
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Gwenborough",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031 x56442",
    "website": "hildegard.org",
    "company": {
      "name": "Romaguera-Crona",
      "catchPhrase": "Multi-layered client-server neural-net",
      "bs": "harness real-time e-markets"
    }
  },
  {
    "id": 2,
    "name": "Ervin Howell",
    "username": "Antonette",
    "email": "Shanna@melissa.tv",
    "address": {
      "street": "Victor Plains",
      "suite": "Suite 879",
      "city": "Wisokyburgh",
      "zipcode": "90566-7771",
      "geo": {
        "lat": "-43.9509",
        "lng": "-34.4618"
      }
    },
    "phone": "010-692-6593 x09125",
    "website": "anastasia.net",
    "company": {
      "name": "Deckow-Crist",
      "catchPhrase": "Proactive didactic contingency",
      "bs": "synergize scalable supply-chains"
    }
  },
  {
    "id": 3,
    "name": "Clementine Bauch",
    "username": "Samantha",
    "email": "Nathan@yesenia.net",
    "address": {
      "street": "Douglas Extension",
      "suite": "Suite 847",
      "city": "McKenziehaven",
      "zipcode": "59590-4157",
      "geo": {
        "lat": "-68.6102",
        "lng": "-47.0653"
      }
    },
    "phone": "1-463-123-4447",
    "website": "ramiro.info",
    "company": {
      "name": "Romaguera-Jacobson",
      "catchPhrase": "Face to face bifurcated interface",
      "bs": "e-enable strategic applications"
    }
  },
  {
    "id": 4,
    "name": "Patricia Lebsack",
    "username": "Karianne",
    "email": "Julianne.OConner@kory.org",
    "address": {
      "street": "Hoeger Mall",
      "suite": "Apt. 692",
      "city": "South Elvis",
      "zipcode": "53919-4257",
      "geo": {
        "lat": "29.4572",
        "lng": "-164.2990"
      }
    },
    "phone": "493-170-9623 x156",
    "website": "kale.biz",
    "company": {
      "name": "Robel-Corkery",
      "catchPhrase": "Multi-tiered zero tolerance productivity",
      "bs": "transition cutting-edge web services"
    }
  },
  {
    "id": 5,
    "name": "Chelsey Dietrich",
    "username": "Kamren",
    "email": "Lucio_Hettinger@annie.ca",
    "address": {
      "street": "Skiles Walks",
      "suite": "Suite 351",
      "city": "Roscoeview",
      "zipcode": "33263",
      "geo": {
        "lat": "-31.8129",
        "lng": "62.5342"
      }
    },
    "phone": "(254)954-1289",
    "website": "demarco.info",
    "company": {
      "name": "Keebler LLC",
      "catchPhrase": "User-centric fault-tolerant solution",
      "bs": "revolutionize end-to-end systems"
    }
  },
  {
    "id": 6,
    "name": "Mrs. Dennis Schulist",
    "username": "Leopoldo_Corkery",
    "email": "Karley_Dach@jasper.info",
    "address": {
      "street": "Norberto Crossing",
      "suite": "Apt. 950",
      "city": "South Christy",
      "zipcode": "23505-1337",
      "geo": {
        "lat": "-71.4197",
        "lng": "71.7478"
      }
    },
    "phone": "1-477-935-8478 x6430",
    "website": "ola.org",
    "company": {
      "name": "Considine-Lockman",
      "catchPhrase": "Synchronised bottom-line interface",
      "bs": "e-enable innovative applications"
    }
  },
  {
    "id": 7,
    "name": "Kurtis Weissnat",
    "username": "Elwyn.Skiles",
    "email": "Telly.Hoeger@billy.biz",
    "address": {
      "street": "Rex Trail",
      "suite": "Suite 280",
      "city": "Howemouth",
      "zipcode": "58804-1099",
      "geo": {
        "lat": "24.8918",
        "lng": "21.8984"
      }
    },
    "phone": "210.067.6132",
    "website": "elvis.io",
    "company": {
      "name": "Johns Group",
      "catchPhrase": "Configurable multimedia task-force",
      "bs": "generate enterprise e-tailers"
    }
  },
  {
    "id": 8,
    "name": "Nicholas Runolfsdottir V",
    "username": "Maxime_Nienow",
    "email": "Sherwood@rosamond.me",
    "address": {
      "street": "Ellsworth Summit",
      "suite": "Suite 729",
      "city": "Aliyaview",
      "zipcode": "45169",
      "geo": {
        "lat": "-14.3990",
        "lng": "-120.7677"
      }
    },
    "phone": "586.493.6943 x140",
    "website": "jacynthe.com",
    "company": {
      "name": "Abernathy Group",
      "catchPhrase": "Implemented secondary concept",
      "bs": "e-enable extensible e-tailers"
    }
  },
  {
    "id": 9,
    "name": "Glenna Reichert",
    "username": "Delphine",
    "email": "Chaim_McDermott@dana.io",
    "address": {
      "street": "Dayna Park",
      "suite": "Suite 449",
      "city": "Bartholomebury",
      "zipcode": "76495-3109",
      "geo": {
        "lat": "24.6463",
        "lng": "-168.8889"
      }
    },
    "phone": "(775)976-6794 x41206",
    "website": "conrad.com",
    "company": {
      "name": "Yost and Sons",
      "catchPhrase": "Switchable contextually-based project",
      "bs": "aggregate real-time technologies"
    }
  },
  {
    "id": 10,
    "name": "Clementina DuBuque",
    "username": "Moriah.Stanton",
    "email": "Rey.Padberg@karina.biz",
    "address": {
      "street": "Kattie Turnpike",
      "suite": "Suite 198",
      "city": "Lebsackbury",
      "zipcode": "31428-2261",
      "geo": {
        "lat": "-38.2386",
        "lng": "57.2232"
      }
    },
    "phone": "024-648-3804",
    "website": "ambrose.net",
    "company": {
      "name": "Hoeger LLC",
      "catchPhrase": "Centralized empowering task-force",
      "bs": "target end-to-end models"
    }
  }
]
```

- Sixth step. We import the json within path /user.
For this write the right path and after import the users.json file.

![firebase4](./firebase6.jpg)

- Seventh step. Now you are ready.You use fetch for access your api
