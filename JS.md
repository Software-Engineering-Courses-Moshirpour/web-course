# JavaScript

## Adding js to HTML

There are basically two ways to add JavaScript to your website.

- Using the `<script>` element and writing JavaScript right in the HTML file
- Adding JavaScript as an external file (this approach is more common and considered best practice)

Example of the first approach:

```html
<script>
  // JavaScript Code
</script>
```

Example of second approach:

```html
<script type="text/javascript" src="file.js"></script>
```

You can put this code either in the header section of your HTML file or at the end, right before the body ends. Based on what approach you choose, your JavaScript file will get loaded either at the beginning or end of page load. Again, as mentioned before, this is considered the best practice of adding JavaScript to your code and most bundle tools, such as [Webpack](https://webpack.js.org/) use this approach.

You will see that when we get to the React section of the course, we don't usually manage these files manually, although it's possible. React applications--regardless of the way you create them (`create-react-app`, Gatsby, Next.js, ..)--they all come with a pre-installed package that will take care of bundling and file management for us. However, it is important to understand the different approaches of adding JavaScript to your website.

You can learn more about adding JavaScript to your web application [here](https://www.w3schools.com/js/js_whereto.asp).

## Datatypes

JavaScript has typed values, not type variables, meaning that for declaring a variable you don't have to specify a type. The type will be determined based on the value that a particular variable holds. These are the buli-in types in JavaScript:

- `string`
- `number`
- `boolean`
- `null`
- `undefined`
- `object`

The following example shows what we mean by typed values and not variables:

```js
var a;
typeof a; // "undefined"

a = "hello world";
typeof a; // "string"

a = 42;
typeof a; // "number"

a = true;
typeof a; // "boolean"

a = undefined;
typeof a; // "undefined"

a = { b: "c" };
typeof a; // "object"
```

It's important to note that in JavaScript, both dictionaries and arrays are `objects`. Object can be used either with the Dot notation or brackets as shown in the following example:

```js
var obj = {
  a: "hello world",
  b: 42,
};

var b = "a";

obj[b]; // "hello world"

obj["b"]; // 42

obj.b; // 42
```

The following example shows an array in JavaScript:

```js
var arr = ["hello world", 42, true];

arr[0]; // "hello world"

arr[1]; // 42

arr[2]; // true

arr.length; // 3

typeof arr; // "object"
```

As you can see at the end of the example, type of the array is `object`, as mentioned earlier.

You can read more about JavaScript datatypes at this [link](https://www.w3schools.com/js/js_datatypes.asp).

## Functions (traditional and arrow functions)

A function is generally a named section of code that can be “called” byname, and the code inside it will be run each time.

For example:

```js
function printAmount() {
  console.log(amount.toFixed(2));
}

var amount = 99.99;

printAmount(); // "99.99"

amount = amount * 2;

printAmount(); // "199.98"
```

Functions can optionally take an argument and return a value back:

```js
function printAmount(amt) {
  console.log(amt.toFixed(2));
}

function formatAmount() {
  return "$" + amount.toFixed(2);
}

var amount = 99.99;

printAmount(amount * 2); // "199.98"

amount = formatAmount();

console.log(amount); // "$99.99"
```

Additionally, you can use arrow functions which are kind of new to JavaScript. Take a look at this example:

```js
// Traditional Function
function (a){
  return a + 100;
}

// Arrow Function Break Down

// 1. Remove the word "function" and place arrow between the argument and opening body bracket
(a) => {
  return a + 100;
}

// 2. Remove the body brackets and word "return" -- the return is implied.
(a) => a + 100;

// 3. Remove the argument parentheses
a => a + 100;
```

The above example shows the situation where you have only one argument. The syntax is a little different where you have more that one argument or no argument at all.

```js
// Traditional Function
function (a, b){
  return a + b + 100;
}

// Arrow Function
(a, b) => a + b + 100;

// Traditional Function (no arguments)
let a = 4;
let b = 2;

function (){
  return a + b + 100;
}

// Arrow Function (no arguments)
let a = 4;
let b = 2;

() => a + b + 100;
```

You can learn more about JavaScript function [here](https://www.w3schools.com/js/js_functions.asp) and specifically about arrow functions [here](https://www.w3schools.com/js/js_arrow_function.asp).

## JavaScript Cool New Features

These features were not initially included in JavaScript, but they were added in recent years. They have been part of JavaScript for years now and will work on any major browser.

### `for..of` Loops

Joining the for and for..in loops from the JavaScript we’re allfamiliar with, ES6 adds a for..of loop, which loops over the set ofvalues produced by an iterator. Take a look at the following example:

```js
const array1 = ["a", "b", "c"];

for (const element of array1) {
  console.log(element);
}

// expected output: "a"
// expected output: "b"
// expected output: "c"
```

You can learn more about `for..of` loop [here](https://www.w3schools.com/js/js_loop_forof.asp`).

### `let`

The let statement declares a block-scoped local variable, optionally initializing it to a value. Take a look at the following example:

```js
let x = 1;

if (x === 1) {
  let x = 2;

  console.log(x);
  // expected output: 2
}

console.log(x);
// expected output: 1
```

You can learn more abot `let` [here](https://www.w3schools.com/js/js_let.asp).

### `const`

Constants are block-scoped, much like variables declared using the let keyword. The value of a constant can't be changed through reassignment, and it can't be redeclared:

```js
const number = 42;

try {
  number = 99;
} catch (err) {
  console.log(err);
  // expected output: TypeError: invalid assignment to const `number'
  // Note - error messages will vary depending on browser
}

console.log(number);
// expected output: 42
```

You can learn more about `const` [here](https://www.w3schools.com/js/js_const.asp).

### Destructuring

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables:

```js
let a, b, rest;
[a, b] = [10, 20];
console.log(a); // 10
console.log(b); // 20

[a, b, ...rest] = [10, 20, 30, 40, 50];
console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40, 50]

({ a, b } = { a: 10, b: 20 });
console.log(a); // 10
console.log(b); // 20

// Stage 4(finished) proposal
({ a, b, ...rest } = { a: 10, b: 20, c: 30, d: 40 });
console.log(a); // 10
console.log(b); // 20
console.log(rest); // {c: 30, d: 40}
```

You can learn more about destructuring [here](https://www.w3docs.com/learn-javascript/destructuring-assignment.html).

### Template literals

Template literals are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them:

```js
let a = 2;
let b = 3;

console.log(`The sum is ${a + b}!`); // The sum is 5!
```

You can learn more about Template Literals [here](https://css-tricks.com/template-literals/).

### `async` and `await`

`async` and `await` were added to JavaScript in 2017. They make async code look more like old-school synchronous code, so they're well worth learning.

The following example is written without using `async/await`. Don't worry if you don't fully understand the code. We will see examples like this in later chapter where we get to the React part of the course.

```js
fetch("coffee.jpg")
  .then((response) => {
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    } else {
      return response.blob();
    }
  })
  .then((myBlob) => {
    let objectURL = URL.createObjectURL(myBlob);
    let image = document.createElement("img");
    image.src = objectURL;
    document.body.appendChild(image);
  })
  .catch((e) => {
    console.log(
      "There has been a problem with your fetch operation: " + e.message
    );
  });
```

Now, let's convert the code and use `async/await` insted:

```js
async function myFetch() {
  let response = await fetch("coffee.jpg");

  if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
  } else {
    let myBlob = await response.blob();

    let objectURL = URL.createObjectURL(myBlob);
    let image = document.createElement("img");
    image.src = objectURL;
    document.body.appendChild(image);
  }
}

myFetch().catch((e) => {
  console.log(
    "There has been a problem with your fetch operation: " + e.message
  );
});
```

You can learn more abot `async/await` [here](https://www.w3schools.com/js/js_async.asp).

### `map`

The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array:

```js
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map((x) => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

You can learn more about `map` [here](https://www.w3schools.com/jsref/jsref_map.asp).

### `filter`

The `filter()` method creates a new array with all elements that pass the test implemented by the provided function:

```js
const words = [
  "spray",
  "limit",
  "elite",
  "exuberant",
  "destruction",
  "present",
];

const result = words.filter((word) => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

You can learn more about `filter` [here](https://www.w3schools.com/jsref/jsref_filter.asp).

### Fetch

The Fetch API provides an interface for fetching resources (including across the network) without the need to refresh the page:

```js
fetch("http://example.com/movies.json")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

We will see a library for making REST API requests when we get to the React part of the course. But in case you are curious about it, the name is [`axios`](https://github.com/axios/axios).

You can learn more about the `fetch` api [here](https://www.w3schools.com/js/js_api_fetch.asp).

## Resources:

- [YDKJY Books](https://www.amazon.ca/You-Dont-Know-JS-Yet/dp/B084DFZ6GW/ref=sr_1_1?crid=22AUG368DP6V6&dchild=1&keywords=you+don%27t+know+js&qid=1614664128&sprefix=you+don%2Caps%2C223&sr=8-1)
- [FreeCodeCamp Video](https://www.youtube.com/watch?v=PkZNo7MFNFg&ab_channel=freeCodeCamp.org)
- [Traversy Media](https://www.youtube.com/watch?v=hdI2bqOjy3c&ab_channel=TraversyMedia)
- [W3School](https://www.w3schools.com/js/DEFAULT.asp)
- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
