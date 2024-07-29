# ES6 Data Manipulation

This repo is created to help understand and practice essential concepts related to data manipulation in ECMAScript 6 (ES6). Below, you'll find a detailed overview of the topics covered in this repository along with practical exercises to reinforce learning them.

## Table of Contents
1. [Array Methods: `map`, `filter`, and `reduce`](#array-methods-map-filter-and-reduce)
2. [Typed Arrays](#typed-arrays)
3. [Set, Map, and Weak Data Structures](#set-map-and-weak-data-structures)

## Array Methods: `map`, `filter`, and `reduce`

### `map` Method
The `map` method creates a new array populated with the results of calling a provided function on every element in the calling array.

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(x => x * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

### `filter` Method
The `filter` method creates a new array with all elements that pass the test implemented by the provided function.

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(x => x % 2 === 0);
console.log(evenNumbers); // [2, 4]
```

### `reduce` Method
The `reduce` method executes a reducer function on each element of the array, resulting in a single output value.

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 0);
console.log(sum); // 15
```

## Typed Arrays
Typed arrays provide a mechanism for accessing raw binary data in JavaScript. They are used for handling binary data in various formats.

### Example
```javascript
const buffer = new ArrayBuffer(16);
const int32View = new Int32Array(buffer);

int32View[0] = 42;
int32View[1] = 84;

console.log(int32View); // Int32Array(4) [42, 84, 0, 0]
```

### Typed Array Types
- `Int8Array`
- `Uint8Array`
- `Uint8ClampedArray`
- `Int16Array`
- `Uint16Array`
- `Int32Array`
- `Uint32Array`
- `Float32Array`
- `Float64Array`

## Set, Map, and Weak Data Structures

### Set
A `Set` is a collection of unique values. It ensures that each value occurs only once.

```javascript
const set = new Set([1, 2, 3, 4, 5, 5]);
console.log(set); // Set(5) {1, 2, 3, 4, 5}

set.add(6);
console.log(set); // Set(6) {1, 2, 3, 4, 5, 6}

set.delete(3);
console.log(set); // Set(5) {1, 2, 4, 5, 6}

console.log(set.has(4)); // true
```

### Map
A `Map` is a collection of key-value pairs where keys can be of any type.

```javascript
const map = new Map();
map.set('a', 1);
map.set('b', 2);
map.set('c', 3);

console.log(map); // Map(3) {"a" => 1, "b" => 2, "c" => 3}

console.log(map.get('b')); // 2

map.delete('a');
console.log(map); // Map(2) {"b" => 2, "c" => 3}

console.log(map.has('c')); // true
```

### WeakSet
A `WeakSet` is a collection of objects only. An object in the `WeakSet` can be garbage-collected if there are no other references to it.

```javascript
let obj1 = {name: 'John'};
let obj2 = {name: 'Doe'};

const weakSet = new WeakSet([obj1, obj2]);
console.log(weakSet.has(obj1)); // true

obj1 = null; // obj1 can be garbage-collected
```

### WeakMap
A `WeakMap` is a collection of key-value pairs where keys are objects and values can be arbitrary values. An object key in the `WeakMap` can be garbage-collected if there are no other references to it.

```javascript
let obj1 = {name: 'John'};
const weakMap = new WeakMap();
weakMap.set(obj1, 'value1');

console.log(weakMap.get(obj1)); // 'value1'

obj1 = null; // obj1 can be garbage-collected
```
