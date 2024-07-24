# ES6 Promises

This repository is designed to help understand and practice essential concepts related to Promises in ECMAScript 6 (ES6). Below, you'll find a detailed overview of the topics covered in this repository along with practical exercises to reinforce your learning.

## Table of Contents
1. [Promises (How, Why, and What)](#promises-how-why-and-what)
2. [Using `then`, `resolve`, and `catch` Methods](#using-then-resolve-and-catch-methods)
3. [Methods of the Promise Object](#methods-of-the-promise-object)
4. [Throw / Try](#throw--try)
5. [The `await` Operator](#the-await-operator)
6. [Using `async` Functions](#using-async-functions)

## Promises (How, Why, and What)

### What is a Promise?
A Promise is an object representing the eventual completion or failure of an asynchronous operation. It allows you to write asynchronous code in a more synchronous fashion, improving code readability and maintainability.

### Why Use Promises?
Promises provide a cleaner and more manageable way to handle asynchronous operations compared to traditional callback-based approaches. They help avoid callback hell and make it easier to handle errors.

### How to Create a Promise
You can create a Promise using the `Promise` constructor which takes a function with two parameters, `resolve` and `reject`.

```javascript
const myPromise = new Promise((resolve, reject) => {
    // Asynchronous operation
    const success = true;

    if (success) {
        resolve('Operation was successful');
    } else {
        reject('Operation failed');
    }
});
```

## Using `then`, `resolve`, and `catch` Methods

### `then` Method
The `then` method is used to handle the result of a resolved Promise.

```javascript
myPromise.then((message) => {
    console.log(message); // 'Operation was successful'
});
```

### `resolve` Method
The `resolve` method is used to mark a Promise as fulfilled and pass a value to the `then` handler.

### `catch` Method
The `catch` method is used to handle errors or rejected Promises.

```javascript
myPromise.catch((error) => {
    console.log(error); // 'Operation failed'
});
```

## Methods of the Promise Object

### `Promise.all`
`Promise.all` takes an array of Promises and resolves when all of them are resolved or rejects when any one of them is rejected.

```javascript
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve, reject) => {
    setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3]).then((values) => {
    console.log(values); // [3, 42, "foo"]
});
```

### `Promise.race`
`Promise.race` takes an array of Promises and resolves or rejects as soon as one of the Promises resolves or rejects.

```javascript
const promise1 = new Promise((resolve, reject) => {
    setTimeout(resolve, 500, 'one');
});

const promise2 = new Promise((resolve, reject) => {
    setTimeout(resolve, 100, 'two');
});

Promise.race([promise1, promise2]).then((value) => {
    console.log(value); // 'two'
});
```

### `Promise.allSettled`
`Promise.allSettled` waits for all Promises to either resolve or reject and returns an array of objects describing the outcome of each Promise.

```javascript
const promise1 = Promise.resolve(3);
const promise2 = new Promise((resolve, reject) => setTimeout(reject, 100, 'error'));
const promise3 = new Promise((resolve, reject) => setTimeout(resolve, 100, 'foo'));

Promise.allSettled([promise1, promise2, promise3]).then((results) => {
    results.forEach((result) => console.log(result.status));
});
// 'fulfilled', 'rejected', 'fulfilled'
```

### `Promise.any`
`Promise.any` takes an array of Promises and resolves as soon as any one of the Promises resolves. If all the Promises are rejected, it returns an AggregateError.

```javascript
const promise1 = Promise.reject('error1');
const promise2 = new Promise((resolve, reject) => setTimeout(resolve, 100, 'foo'));
const promise3 = new Promise((resolve, reject) => setTimeout(resolve, 200, 'bar'));

Promise.any([promise1, promise2, promise3]).then((value) => {
    console.log(value); // 'foo'
});
```

## Throw / Try

### Throwing Errors
Errors can be thrown using the `throw` keyword, which can then be caught in a `catch` block.

```javascript
try {
    throw new Error('Something went wrong!');
} catch (error) {
    console.log(error.message); // 'Something went wrong!'
}
```

### Using `catch` for Error Handling
Use `catch` to handle errors in Promises.

```javascript
myPromise.catch((error) => {
    console.log(error); // 'Operation failed'
});
```

## The `await` Operator
The `await` operator is used to wait for a Promise to resolve or reject. It can only be used inside an `async` function.

```javascript
async function myFunction() {
    try {
        const result = await myPromise;
        console.log(result); // 'Operation was successful'
    } catch (error) {
        console.log(error); // 'Operation failed'
    }
}

myFunction();
```

## Using `async` Functions
An `async` function allows the use of `await` within its body and automatically returns a Promise.

```javascript
async function fetchData() {
    try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}

fetchData();
```
