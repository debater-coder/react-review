---
marp: true
class: invert
---

# React Concepts

---

# Functional Programming

Overview: https://www.youtube.com/watch?v=HlgG395PQWw&ab_channel=Coderized

---

# 4 ways to define a function

```js
// When using this method, it doesn't matter which order you define the function and call it
function area_triangle(base, height) {
  return 0.5 * base * height;
}

// This assigns the function to a variable so you must define the function before calling it
const area_triangle = function (base, height) {
  return 0.5 * base * height;
};

// Arrow function shorthand
const area_triangle = (base, height) => {
  return 0.5 * base * height;
};

// When using arrow functions, if the function is only one line, you can omit the curly braces and the return keyword
const area_triangle = (base, height) => 0.5 * base * height;
```

**Task: Practice defining functions using all 4 methods**

---

# Function scope

Functions have their own "scope", meaning that variables defined inside a function are not accessible outside of the function.

```js
let x = 10;

function myFunction() {
  let y = 20;
  console.log(x); // 10
  console.log(y); // 20
}

console.log(x); // 10
console.log(y); // ReferenceError: y is not defined
```

When a function accesses a variable in the outer scope, it is called a "closure".

---

# Callbacks

A callback is a function that is passed as an argument to another function and is executed after the completion of the first function.

```js
function greet(name, callback) {
  console.log("Hello " + name);
  callback();
}

function callMe() {
  console.log("I am a callback function");
}

greet("John", callMe);
```

What output will this code produce?

---

# Higher Order Functions

A callback is a specific example of higher order functions. A higher order function is a function that takes a function as an argument, or returns a function.

```js
function hello() {
  console.log("Hello");
}

// setInterval is a higher order function that is built into JavaScript
// It takes a function as the first argument and a time in milliseconds as the second argument
// It will call the function every time the time interval elapses
setInterval(hello, 1000);
```

---

# Higher Order Functions

Note the code can be shortened using an arrow function

```js
setInterval(() => console.log("Hello"), 1000);
```

---

# JavaScript Promises

Overview: https://www.youtube.com/watch?v=RvYYCGs45L4&ab_channel=Fireship

---

# `async` and `await` in JavaScript

```js
// Fetch is an example of a function that returns a promise
fetch("https://jsonplaceholder.typicode.com/users")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.log(error));
```

```js
// This code does the same thing as the previous code, but it is easier to read
try {
  const response = await fetch("https://jsonplaceholder.typicode.com/users");

  const data = await response.json();

  console.log(data);
} catch (error) {
  console.log(error);
}
```

---

# Functional Programming approach to loops

Loops are generally not used in functional programming as they use mutable variables and are prone to off-by-one errors.

Instead, we use higher order functions like `map`, `filter`, and `reduce`.

```js
const numbers = [1, 2, 3, 4, 5];

const doubled = numbers.map((number) => number * 2);

const evens = numbers.filter((number) => number % 2 === 0);

const sum = numbers.reduce((total, number) => total + number, 0);

console.log(doubled); // [2, 4, 6, 8, 10]
console.log(evens); // [2, 4]
console.log(sum); // 15
```

Exercise: Write a function that takes an array of numbers and returns the sum of the squares of the even numbers.

---

# Arrays and Objects in JavaScript

Arrays and objects are composite data types in JavaScript. They can contain other arrays and objects, as well as primitive data types (numbers and strings).

```js
const person = {
  name: "John",
  age: 30,
  address: {
    street: "123 JavaScript St",
    city: "Sydney",
  },
  hobbies: ["reading", "cooking", "hiking"],
};

console.log(person.name); // John
console.log(person.address.city); // New York
console.log(person.hobbies[1]); // cooking
person.hobbies.push("biking");
console.log(person.hobbies); // ["reading", "cooking", "hiking", "biking"]
```

---

# Array and Object Destructuring

```js
const person = {
  name: "John",
  age: 30,
  address: {
    street: "123 JavaScript St",
    city: "Sydney",
  },
  hobbies: ["reading", "cooking", "hiking"],
};

const { name, age, address, hobbies } = person;

console.log(name); // John
console.log(age); // 30
console.log(address.city); // Sydney
console.log(hobbies); // ["reading", "cooking", "hiking"]
```

---

# Array and Object Destructuring

```js
const numbers = [1, 2, 3, 4, 5];

const [apple, banana, orange] = numbers;

console.log(banana);
console.log(orange);
console.log(apple);
```

What will be the output of this code?

---

# Parameter Destructuring

```js
function printPerson({ name, age, address, hobbies }) {
  console.log(name);
  console.log(age);
  console.log(address.city);
  console.log(hobbies);
}

printPerson(person);
```

---

# React Concepts

---

# JSX

JSX is a syntax extension for JavaScript that allows you to write HTML-like code in your JavaScript files.

```jsx
const element = <h1>Hello, world!</h1>;
```

A compiler transforms JSX into regular JavaScript.

This is what it looks like afterwards

```js
const element = React.createElement("h1", null, "Hello, world!");
```

You almost never have to write this yourself, but it's helpful to understand what's happening under the hood.

---

# Rendering JSX

React is a library that "renders" JSX into the DOM. This is what it looks like:

```jsx
import { createRoot } from "react-dom/client";

const root = createRoot(document.getElementById("root"));
root.render(<h1>Hello, World!</h1>);
```

Rendering: https://react.dev/learn/render-and-commit

---

# Components

Components are the building blocks of a React application. They are reusable pieces of code that can be used to build a user interface.

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
