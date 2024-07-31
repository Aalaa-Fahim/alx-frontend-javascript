# TypeScript

This repository covers fundamental concepts of TypeScript, providing a solid foundation for working with basic types, interfaces, classes, functions, DOM manipulation, generics, namespaces, and more.

## Table of Contents
1. [Basic Types in TypeScript](#basic-types-in-typescript)
2. [Interfaces, Classes, and Functions](#interfaces-classes-and-functions)
3. [How to Work with the DOM and TypeScript](#how-to-work-with-the-dom-and-typescript)
4. [Generic Types](#generic-types)
5. [How to Use Namespaces](#how-to-use-namespaces)
6. [How to Merge Declarations](#how-to-merge-declarations)
7. [How to Use an Ambient Namespace to Import an External Library](#how-to-use-an-ambient-namespace-to-import-an-external-library)
8. [Basic Nominal Typing with TypeScript](#basic-nominal-typing-with-typescript)

## Basic Types in TypeScript

TypeScript, like JavaScript, supports various basic types. Here are some common ones:

### Number
```typescript
let age: number = 25;
```

### String
```typescript
let name: string = "John";
```

### Boolean
```typescript
let isStudent: boolean = true;
```

### Array
```typescript
let numbers: number[] = [1, 2, 3, 4];
let fruits: Array<string> = ["Apple", "Banana", "Cherry"];
```

### Tuple
A tuple allows you to express an array with a fixed number of elements whose types are known.

```typescript
let person: [string, number];
person = ["John", 25]; // OK
```

### Enum
Enums allow you to define a set of named constants.

```typescript
enum Color {Red, Green, Blue}
let c: Color = Color.Green;
```

### Any
The `any` type can be used to store a value of any type.

```typescript
let randomValue: any = 10;
randomValue = "Hello"; // OK
randomValue = true; // OK
```

## Interfaces, Classes, and Functions

### Interfaces
Interfaces define the shape of objects.

```typescript
interface Person {
    name: string;
    age: number;
}

let john: Person = {
    name: "John",
    age: 25
};
```

### Classes
Classes are blueprints for creating objects.

```typescript
class Student {
    name: string;
    age: number;

    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }

    greet() {
        return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
    }
}

let student = new Student("John", 25);
console.log(student.greet()); // Hello, my name is John and I am 25 years old.
```

### Functions
Functions are the basic building blocks in TypeScript.

```typescript
function add(a: number, b: number): number {
    return a + b;
}

let sum = add(5, 10);
console.log(sum); // 15
```

## How to Work with the DOM and TypeScript

TypeScript can interact with the Document Object Model (DOM) to manipulate web pages.

```typescript
const button = document.querySelector('button');

button?.addEventListener('click', () => {
    console.log('Button clicked!');
});
```

In this example, we select a button from the DOM and add a click event listener to it.

## Generic Types

Generics allow you to create reusable components.

```typescript
function identity<T>(arg: T): T {
    return arg;
}

let output1 = identity<string>("Hello");
let output2 = identity<number>(100);

console.log(output1); // Hello
console.log(output2); // 100
```

## How to Use Namespaces

Namespaces are used to organize code into logical groups and to prevent name collisions.

```typescript
namespace Geometry {
    export class Circle {
        constructor(public radius: number) {}

        area(): number {
            return Math.PI * this.radius * this.radius;
        }
    }
}

let circle = new Geometry.Circle(10);
console.log(circle.area()); // 314.1592653589793
```

## How to Merge Declarations

Merging declarations allows multiple declarations with the same name to be combined into a single declaration.

```typescript
interface Car {
    model: string;
}

interface Car {
    year: number;
}

let myCar: Car = {
    model: "Toyota",
    year: 2020
};
```

## How to Use an Ambient Namespace to Import an External Library

Ambient namespaces allow you to describe the shape of libraries not written in TypeScript.

```typescript
declare namespace myLibrary {
    function doSomething(): void;
}

myLibrary.doSomething();
```

In this example, we declare an ambient namespace for an external library and use it.

## Basic Nominal Typing with TypeScript

Nominal typing ensures that types are not interchangeable unless explicitly specified.

```typescript
type UserID = { _id: string };

function getUser(id: UserID) {
    console.log(id._id);
}

let userId: UserID = { _id: "12345" };
getUser(userId); // OK

// getUser({ _id: "67890" }); // Error: Argument of type '{ _id: string; }' is not assignable to parameter of type 'UserID'.
```
