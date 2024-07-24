# ES6 Basics

This repository is designed to help understand and practice essential concepts introduced in ECMAScript 6 (ES6), a significant update to JavaScript that brought many new features and improvements. Below, you'll find a detailed overview of the topics covered in this repository.

## Table of Contents
1. [What is ES6?](#what-is-es6)
2. [New Features Introduced in ES6](#new-features-introduced-in-es6)
3. [Difference Between a Constant and a Variable](#difference-between-a-constant-and-a-variable)
4. [Block-Scoped Variables](#block-scoped-variables)
5. [Arrow Functions and Default Parameters](#arrow-functions-and-default-parameters)
6. [Rest and Spread Function Parameters](#rest-and-spread-function-parameters)
7. [String Templating in ES6](#string-templating-in-es6)
8. [Object Creation and Properties in ES6](#object-creation-and-properties-in-es6)
9. [Iterators and For-Of Loops](#iterators-and-for-of-loops)

## What is ES6?
ES6, also known as ECMAScript 2015, is the sixth edition of the ECMAScript standard. It is a major update to JavaScript, adding new syntax and features that make it easier to write and maintain complex code. ES6 is a significant improvement over previous versions, offering better performance, readability, and development tools.

## New Features Introduced in ES6
ES6 introduced several new features and improvements, including but not limited to:
- Let and const keywords for variable declarations
- Arrow functions
- Template literals
- Default parameters
- Rest and spread operators
- Enhanced object literals
- Destructuring assignment
- Promises
- Classes
- Modules
- Iterators and for-of loops
- Symbols

## Difference Between a Constant and a Variable
In ES6, you can declare variables using `var`, `let`, or `const`. 

- `var`: Declares a function-scoped or globally-scoped variable.
- `let`: Declares a block-scoped variable.
- `const`: Declares a block-scoped variable that cannot be reassigned after its initial assignment. However, the value it holds can still be mutable (e.g., objects and arrays).

```javascript
var x = 1; // Function-scoped
let y = 2; // Block-scoped
const z = 3; // Block-scoped, constant value
```

## Block-Scoped Variables
`let` and `const` provide block scope, which means they are only accessible within the block they are declared. This helps prevent issues with variable hoisting and scope pollution.

```javascript
if (true) {
    let a = 10;
    const b = 20;
    console.log(a); // 10
    console.log(b); // 20
}
console.log(a); // ReferenceError: a is not defined
console.log(b); // ReferenceError: b is not defined
```

## Arrow Functions and Default Parameters
Arrow functions provide a concise syntax for writing functions and lexically bind the `this` value.

```javascript
const add = (x, y = 10) => x + y;
console.log(add(5)); // 15
console.log(add(5, 15)); // 20
```

## Rest and Spread Function Parameters
The rest parameter syntax allows a function to accept an indefinite number of arguments as an array. The spread operator allows an array to be expanded into individual elements.

```javascript
const sum = (...numbers) => numbers.reduce((acc, curr) => acc + curr, 0);
console.log(sum(1, 2, 3, 4)); // 10

const arr = [1, 2, 3];
const newArr = [...arr, 4, 5, 6];
console.log(newArr); // [1, 2, 3, 4, 5, 6]
```

## String Templating in ES6
Template literals allow for easier string interpolation and multi-line strings.

```javascript
const name = 'John';
const greeting = `Hello, ${name}!`;
console.log(greeting); // Hello, John!

const multiLineString = `
This is a
multi-line
string.
`;
console.log(multiLineString);
```

## Object Creation and Properties in ES6
ES6 simplifies object creation and property assignment.

```javascript
const name = 'Alaa';
const age = 23;

const person = {
    name,
    age,
    greet() {
        console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
    }
};

person.greet(); // Hello, my name is Alaa and I am 23 years old.
```

## Iterators and For-Of Loops
ES6 introduces the `for-of` loop, which allows iteration over iterable objects like arrays, strings, and more.

```javascript
const array = [1, 2, 3, 4, 5];

for (const value of array) {
    console.log(value);
}
// Output: 1 2 3 4 5
```
