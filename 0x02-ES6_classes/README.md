# ES6 Classes

This repository is designed to help understand and practice essential concepts related to classes in ECMAScript 6 (ES6). Below, you'll find a detailed overview of the topics covered in this repository along with practical exercises to reinforce your learning.

## Table of Contents
1. [How to Define a Class](#how-to-define-a-class)
2. [How to Add Methods to a Class](#how-to-add-methods-to-a-class)
3. [Why and How to Add a Static Method to a Class](#why-and-how-to-add-a-static-method-to-a-class)
4. [How to Extend a Class from Another](#how-to-extend-a-class-from-another)
5. [Metaprogramming and Symbols](#metaprogramming-and-symbols)

## How to Define a Class
In ES6, a class is defined using the `class` keyword. A class can have a constructor method to initialize its properties.

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}

const john = new Person('John', 30);
console.log(john.name); // John
console.log(john.age); // 30
```

## How to Add Methods to a Class
Methods are functions that belong to an object. In ES6, you can define methods directly inside a class.

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    greet() {
        return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
    }
}

const john = new Person('John', 30);
console.log(john.greet()); // Hello, my name is John and I am 30 years old.
```

## Why and How to Add a Static Method to a Class
Static methods are called on the class itself, not on instances of the class. They are used to create utility functions that are related to the class but don't operate on instance data.

### Why Use Static Methods?
Static methods can be useful for creating helper functions or utilities that are relevant to the class but don't need access to instance-specific data.

### How to Define a Static Method
Use the `static` keyword to define a static method.

```javascript
class MathHelper {
    static add(x, y) {
        return x + y;
    }
}

console.log(MathHelper.add(5, 10)); // 15
```

## How to Extend a Class from Another
Class inheritance allows you to create a new class based on an existing class. Use the `extends` keyword to create a subclass.

```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} makes a sound.`);
    }
}

class Dog extends Animal {
    speak() {
        console.log(`${this.name} barks.`);
    }
}

const dog = new Dog('Rex');
dog.speak(); // Rex barks.
```

## Metaprogramming and Symbols
Metaprogramming is a programming technique where programs have the ability to treat other programs as their data. In ES6, metaprogramming can be achieved using Symbols and other reflective capabilities.

### Symbols
Symbols are unique and immutable data types that can be used as object property keys. They provide a way to create private properties for objects.

```javascript
const privateKey = Symbol('privateKey');

class MyClass {
    constructor(value) {
        this[privateKey] = value;
    }

    getPrivateValue() {
        return this[privateKey];
    }
}

const instance = new MyClass('secret');
console.log(instance.getPrivateValue()); // secret
console.log(instance.privateKey); // undefined
```

### Reflect API
The Reflect API provides methods for interceptable JavaScript operations, making it easier to perform metaprogramming.

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}

const person = Reflect.construct(Person, ['John', 30]);
console.log(person.name); // John
console.log(person.age); // 30
```
