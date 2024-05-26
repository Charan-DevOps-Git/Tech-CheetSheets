# Basic Syntax
```
// Single line comment

/*
    Multi-line comment
*/

// Variables
let x = 10;
const y = 20;
var z = 30;

// Functions
function greet(name) {
    return `Hello, ${name}!`;
}

console.log(greet("World")); // Output: Hello, World!
```

# Data Types

- Number: let num = 10;
- String: let str = "Hello";
- Boolean: let isTrue = true;
- Array: let arr = [1, 2, 3];
- Object: let obj = { key: "value" };
- Undefined: let undef;
- Null: let empty = null;
  
# Operators
- Arithmetic: +, -, *, /, %
- Assignment: =, +=, -=, *=, /=
- Comparison: ==, ===, !=, !==, >, <, >=, <=
- Logical: &&, ||, !
- Ternary: condition ? expr1 : expr2

# Control Structures
- if/else
```
if (x > 10) {
    console.log("x is greater than 10");
} else {
    console.log("x is less than or equal to 10");
}
```
- switch
```
switch (x) {
    case 10:
        console.log("x is 10");
        break;
    default:
        console.log("x is not 10");
}
```
- for loop
```
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```
- while loop
```
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

# Functions

- Function Declaration
```
function sum(a, b) {
    return a + b;
}
```
- Function Expression
```
const sum = function(a, b) {
    return a + b;
};
```
- Arrow Function
```
const sum = (a, b) => a + b;
```

# ES6 Features
# let and const

- let: Block-scoped variable.
- const: Block-scoped constant.
```
let a = 10;
const b = 20;
```

# Template Literals
```
const name = "World";
console.log(`Hello, ${name}!`); // Output: Hello, World!
```

# Destructuring

- Array Destructuring
```
const [a, b] = [1, 2];
```

- Object Destructuring
```
const { name, age } = { name: "Alice", age: 25 };
```

# Default Parameters
```
function multiply(a, b = 1) {
    return a * b;
}
```

# Rest Parameters and Spread Operator

- Rest Parameters
```
function sum(...numbers) {
    return numbers.reduce((acc, num) => acc + num, 0);
}
```

- Spread Operator
```
const arr = [1, 2, 3];
const newArr = [...arr, 4, 5];
```

# Arrow Functions
```
const greet = name => `Hello, ${name}!`;
```

# Promises
```
const promise = new Promise((resolve, reject) => {
    // Asynchronous operation
    if (/* success */) {
        resolve("Success!");
    } else {
        reject("Error!");
    }
});

promise
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

# Async/Await
```
async function fetchData() {
    try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
```

# Classes
```
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    greet() {
        console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
    }
}

const alice = new Person('Alice', 25);
alice.greet(); // Output: Hello, my name is Alice and I am 25 years old.
```

# Modules

- Exporting
```
// module.js
export const name = "Alice";
export function greet() {
    console.log(`Hello, ${name}!`);
}
```
- Importing
```
// main.js
import { name, greet } from './module.js';
console.log(name); // Output: Alice
greet(); // Output: Hello, Alice!
```

# Map, Set, WeakMap, WeakSet

- Map
```
const map = new Map();
map.set('key', 'value');
console.log(map.get('key')); // Output: value
```

- Set
```
const set = new Set();
set.add(1);
set.add(2);
set.add(2); // Duplicates are ignored
console.log(set.size); // Output: 2
```

- WeakMap
```
const weakMap = new WeakMap();
const obj = {};
weakMap.set(obj, 'value');
console.log(weakMap.get(obj)); // Output: value
```

- WeakSet
```
const weakSet = new WeakSet();
const obj = {};
weakSet.add(obj);
console.log(weakSet.has(obj)); // Output: true
```

# Resources
[Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
