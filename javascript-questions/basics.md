# JavaScript Basics Interview Questions

## Table of Contents

- [ ] [What are the different data types in JavaScript?](#1-what-are-the-different-data-types-in-javascript)
- [ ] [What is the difference between `var`, `let`, and `const`?](#2-what-is-the-difference-between-var-let-and-const)
- [ ] [Explain hoisting in JavaScript.](#3-explain-hoisting-in-javascript)
- [ ] [What are the differences between `==` and `===` in JavaScript?](#4-what-are-the-differences-between-==-and-===-in-javascript)
- [ ] [What is a closure in JavaScript?](#5-what-is-a-closure-in-javascript)
- [ ] [What is the difference between `null` and `undefined` in JavaScript?](#6-what-is-the-difference-between-null-and-undefined-in-javascript)
- [ ] [Explain the concept of "this" in JavaScript.](#7-explain-the-concept-of-this-in-javascript)
- [ ] [What is the event loop in JavaScript?](#8-what-is-the-event-loop-in-javascript)
- [ ] [What is the difference between an array and an object in JavaScript?](#9-what-is-the-difference-between-an-array-and-an-object-in-javascript)
- [ ] [How do you handle errors in JavaScript?](#10-how-do-you-handle-errors-in-javascript)
- [ ] [What is the difference between `call()`, `apply()`, and `bind()`?](#11-what-is-the-difference-between-call-apply-and-bind)
- [ ] [What are `setTimeout()` and `setInterval()` methods?](#12-what-are-settimeout-and-setinterval-methods)
- [ ] [What is a promise in JavaScript?](#13-what-is-a-promise-in-javascript)
- [ ] [What is the `window` object in JavaScript?](#14-what-is-the-window-object-in-javascript)
- [ ] [What is the difference between synchronous and asynchronous code in JavaScript?](#15-what-is-the-difference-between-synchronous-and-asynchronous-code-in-javascript)
- [ ] [What is the purpose of the `bind()` method in JavaScript?](#16-what-is-the-purpose-of-the-bind-method-in-javascript)
- [ ] [How do you create a private variable in JavaScript?](#17-how-do-you-create-a-private-variable-in-javascript)
- [ ] [What is event delegation in JavaScript?](#18-what-is-event-delegation-in-javascript)
- [ ] [How can you remove an element from an array in JavaScript?](#19-how-can-you-remove-an-element-from-an-array-in-javascript)
- [ ] [What is a `singleton` in JavaScript?](#20-what-is-a-singleton-in-javascript)
- [ ] [What is the purpose of the `try...catch` block in JavaScript?](#21-what-is-the-purpose-of-the-trycatch-block-in-javascript)
- [ ] [How can you check if an object is an array in JavaScript?](#22-how-can-you-check-if-an-object-is-an-array-in-javascript)
- [ ] [How can you check if a string is a palindrome in JavaScript?](#23-how-can-you-check-if-a-string-is-a-palindrome-in-javascript)

---

## 1. What are the different data types in JavaScript?

**Answer**: JavaScript has six primitive data types:

- **`Undefined`**: A variable that has been declared but not assigned a value.
- **`Null`**: Represents the intentional absence of any object value.
- **`Boolean`**: Represents a logical value, `true` or `false`.
- **`Number`**: Represents both integer and floating-point numbers.
- **`String`**: Represents a sequence of characters.
- **`Symbol`**: A unique and immutable value used as an identifier for object properties (added in ES6).

And one non-primitive data type:

- **`Object`**: A collection of key-value pairs.

**Example**:

```javascript
let number = 42; // Number
let name = "John"; // String
let isActive = true; // Boolean
let person = { name: "Alice", age: 30 }; // Object
let undefinedVar; // Undefined
let nothing = null; // Null
```

## 2. What is the difference between `var`, `let`, and `const`?

### **Answer**:

- **`var`**:
  - Declares a variable that is function-scoped or globally-scoped (if declared outside any function).
  - It can be re-declared and updated within its scope.
- **`let`**:

  - Declares a block-scoped variable, meaning it is only accessible within the block where it is declared.
  - It can be updated, but **cannot** be re-declared within the same block.

- **`const`**:
  - Declares a block-scoped variable, but the value **cannot** be reassigned after its initial assignment.
  - It must be initialized with a value when declared.

### **Example**:

```javascript
var x = 1; // function-scoped
let y = 2; // block-scoped
const z = 3; // block-scoped, cannot be changed
x = 10; // works
y = 20; // works
z = 30; // Error: Assignment to constant variable.
```

Key Differences:

- **`Re-declaration:`**:
  var allows redeclaration within the same scope, while let and const do not.

- **`Scope:`**:
  var is function-scoped, meaning it is accessible throughout the function in which it is declared.
  let and const are block-scoped, meaning they are only accessible within the nearest enclosing block (e.g., inside an if statement, loop, or function).

- **`Re-assignment:`**: var and let allow re-assignment of values.
  const does not allow re-assignment, making it ideal for constants.

## 3. Explain hoisting in JavaScript.

**Answer**: Hoisting is JavaScript's default behavior of moving variable and function declarations to the top of their scope (whether they are global or within a function). However, only declarations are hoisted, not initializations.

**Example**:

```javascript
console.log(a); // undefined, due to hoisting
var a = 5; // Declaration is hoisted, but initialization remains at original place

foo(); // "Hello, World!" - function declarations are hoisted
function foo() {
  console.log("Hello, World!");
}
```

- `var a` is hoisted to the top, but its assignment happens at runtime, hence it outputs `undefined`.
- The `foo()` function is hoisted completely, so it can be called before its declaration.

---

## 4. What are the differences between `==` and `===` in JavaScript?

**Answer**:

- **`==`**: Compares two values for equality, performing type coercion if the types are different (e.g., a string can be compared to a number).
- **`===`**: Compares both the value and the type, without type coercion. This is known as the "strict equality" operator.

**Example**:

```javascript
5 == "5"; // true (type coercion happens)
5 === "5"; // false (different types, no coercion)
```

---

## 5. What is a closure in JavaScript?

**Answer**: A closure is a function that retains access to its lexical scope, even when the function is executed outside that scope. This means inner functions have access to variables from their outer functions, even after the outer function has finished execution.

**Example**:

```javascript
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}

const increment = outer();
increment(); // 1
increment(); // 2
```

- In this example, `inner()` has access to `count`, even after `outer()` has finished executing, demonstrating closure.

---

## 6. What is the difference between `null` and `undefined` in JavaScript?

**Answer**:

- **`undefined`**: A variable that has been declared but not assigned a value is automatically assigned `undefined`.
- **`null`**: A value explicitly assigned to a variable to indicate the absence of any object value.

**Example**:

```javascript
let a; // undefined (variable declared but not initialized)
let b = null; // null (intentionally assigned no value)
```

---

## 7. Explain the concept of "this" in JavaScript.

**Answer**: The keyword `this` refers to the context in which a function is called. Its value dep```s on how the function is invoked.

- **In a regular function**, `this` refers to the global object (`window` in browsers).
- **In a method**, `this` refers to the object that the method belongs to.
- **In a constructor function**, `this` refers to the newly created instance.

**Example**:

```javascript
// Regular function
function show() {
  console.log(this); // In browser: window object
}

// Object method
const obj = {
  name: "John",
  greet: function () {
    console.log(this.name); // 'this' refers to obj
  },
};
obj.greet(); // "John"
```

---

## 8. What is the event loop in JavaScript?

**Answer**: The event loop is a mechanism that allows JavaScript to handle asynchronous operations like events, timers, and I/O. It works by using a call stack and an event queue. When the call stack is empty, the event loop picks up events from the queue and executes them.

**Example**:

````javascript
console.log("```javascript");

setTimeout(() => {
  console.log("Inside setTimeout");
}, 0);

console.log("```");
````

- Output:

```javascript
Inside setTimeout
```

- Even though the `setTimeout()` is set to 0ms, it is put in the event queue and executed after the current execution context is finished.

---

## 9. What is the difference between an array and an object in JavaScript?

**Answer**:

- **Array**: An ordered list of values, accessed by index. Arrays are typically used when order matters.
- **Object**: A collection of key-value pairs. Objects are used when you need to group related data together, often with non-numeric keys.

**Example**:

```javascript
let arr = [1, 2, 3]; // Array
let obj = { name: "Alice", age: 30 }; // Object
```

---

## 10. How do you handle errors in JavaScript?

**Answer**: JavaScript provides `try...catch` blocks to handle errors without crashing the program. You can catch synchronous errors in a `try` block and handle them in a `catch` block.

**Example**:

```javascript
try {
  let result = someFunction();
} catch (error) {
  console.error(error); // Logs error message
}
```

---

## 11. What is the difference between `call()`, `apply()`, and `bind()`?

**Answer**:

- **`call()`**: Immediately invokes a function with a specific `this` value and arguments passed individually.
- **`apply()`**: Immediately invokes a function with a specific `this` value and arguments passed as an array.
- **`bind()`**: Returns a new function with a fixed `this` value, and it can be invoked later.

**Example**:

```javascript
function greet(name) {
  console.log(`Hello, ${name}`);
}

greet.call(null, "Alice"); // "Hello, Alice"
greet.apply(null, ["Bob"]); // "Hello, Bob"

const boundGreet = greet.bind(null, "Charlie");
boundGreet(); // "Hello, Charlie"
```

---

## 12. What are `setTimeout()` and `setInterval()` methods?

**Answer**:

- **`setTimeout()`**: Executes a function once after a specified delay (in milliseconds).
- **`setInterval()`**: Repeatedly executes a function at specified intervals (in milliseconds).

**Example**:

```javascript
setTimeout(() => console.log("Hello after 2 seconds"), 2000);
setInterval(() => console.log("Hello every 2 seconds"), 2000);
```

---

## 13. What is a promise in JavaScript?

**Answer**: A `Promise` is an object representing the eventual completion (or failure) of an asynchronous operation. It is in one of three states:

- **P```ing**: The promise is still being processed.
- **Fulfilled**: The promise has been resolved successfully.
- **Rejected**: The promise has been rejected.

# JavaScript Basics Interview Questions

## 14. What is the `window` object in JavaScript?

**Answer**: The `window` object represents the global context in the browser environment. It is the top-level object that holds properties, methods, and events that are accessible globally across your JavaScript code. In a browser, the `window` object includes things like the `document` object, the `console`, and the `localStorage`.

**Example**:

```javascript
console.log(window); // Accesses the window object

// The window object has properties such as:
console.log(window.document); // Accesses the DOM (Document Object Model)
console.log(window.localStorage); // Accesses local storage
```

---

## 15. What is the difference between synchronous and asynchronous code in JavaScript?

**Answer**:

- **Synchronous code**: Executes sequentially, one operation after the other. The next operation ```javascripts only when the previous one has completed.
- **Asynchronous code**: Executes indep```ently of the main program flow. It allows you to perform operations, like reading files or fetching data, without blocking the execution of other code.

**Example**:

````javascript
// Synchronous
console.log("```javascript");
console.log("Middle");
console.log("```");

// Asynchronous
console.log("```javascript");
setTimeout(() => {
  console.log("Middle");
}, 2000); // This will run after 2 seconds
console.log("```"); // Runs immediately after "```javascript"
````

---

## 16. What is the purpose of the `bind()` method in JavaScript?

**Answer**: The `bind()` method is used to create a new function that, when called, has its `this` value set to a specific object. It can also accept arguments that are prep```ed to the arguments of the function when it is later invoked.

**Example**:

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

const greetPerson = greet.bind(null, "Alice");
greetPerson(); // "Hello, Alice!"
```

---

## 17. How do you create a private variable in JavaScript?

**Answer**: In JavaScript, private variables can be created using closures. By using a closure, you can create private variables that are not accessible outside the function but can be manipulated by inner functions.

**Example**:

```javascript
function createCounter() {
  let count = 0; // Private variable
  return {
    increment: function () {
      count++;
      return count;
    },
    decrement: function () {
      count--;
      return count;
    },
    getCount: function () {
      return count;
    },
  };
}

const counter = createCounter();
console.log(counter.increment()); // 1
console.log(counter.increment()); // 2
console.log(counter.getCount()); // 2 (private count variable)
```

---

## 18. What is event delegation in JavaScript?

**Answer**: Event delegation is a technique where you attach a single event listener to a parent element instead of adding separate event listeners to each child element. This is useful for dynamically added elements and improves performance by reducing the number of event listeners.

**Example**:

```javascript
document.querySelector("#parent").addEventListener("click", function (event) {
  if (event.target && event.target.matches("button.classname")) {
    console.log("Button clicked:", event.target);
  }
});
```

---

## 19. How can you remove an element from an array in JavaScript?

**Answer**: You can remove an element from an array using methods like `splice()`, `filter()`, or `pop()`. The choice of method dep```s on whether you know the index, the value, or if you want to modify the array in place.

**Example**:

```javascript
let arr = [1, 2, 3, 4, 5];

// Using splice (removes element by index)
arr.splice(2, 1); // Removes element at index 2
console.log(arr); // [1, 2, 4, 5]

// Using filter (removes element by value)
arr = arr.filter((value) => value !== 4); // Removes all occurrences of 4
console.log(arr); // [1, 2, 5]
```

---

## 20. What is a `singleton` in JavaScript?

**Answer**: A singleton is a design pattern where a class or object ensures that only one instance is created. This pattern restricts the instantiation of a class to a single object and provides a global point of access to it.

**Example**:

```javascript
const Singleton = (function () {
  let instance;

  function createInstance() {
    return { name: "Singleton" };
  }

  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    },
  };
})();

const instance1 = Singleton.getInstance();
const instance2 = Singleton.getInstance();

console.log(instance1 === instance2); // true
```

---

## 21. What is the purpose of the `try...catch` block in JavaScript?

**Answer**: The `try...catch` block is used to handle exceptions (errors) in JavaScript. Code that might throw an error is placed inside the `try` block, and if an error occurs, it is caught and handled in the `catch` block.

**Example**:

```javascript
try {
  let result = someFunction(); // May throw an error
} catch (error) {
  console.error("An error occurred:", error); // Handles error
}
```

---

## 22. How can you check if an object is an array in JavaScript?

**Answer**: You can use `Array.isArray()` to check if an object is an array. This method returns `true` if the object is an array and `false` otherwise.

**Example**:

```javascript
let arr = [1, 2, 3];
let obj = { name: "John" };

console.log(Array.isArray(arr)); // true
console.log(Array.isArray(obj)); // false
```

---

## 23. How can you check if a string is a palindrome in JavaScript?

**Answer**: A palindrome is a string that reads the same forward and backward. You can check if a string is a palindrome by reversing the string and comparing it to the original string.

**Example**:

```javascript
function isPalindrome(str) {
  const reversed = str.split("").reverse().join("");
  return str === reversed;
}

console.log(isPalindrome("racecar")); // true
console.log(isPalindrome("hello")); // false
```
