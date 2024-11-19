80 JavaScript interview questions and answers, ranging from **Fundamentals** to **Advanced Concepts**, with code examples where applicable. 

---

### **Basic JavaScript Questions**

1. **What is JavaScript?**
   - **Answer:** JavaScript is a high-level, interpreted programming language primarily used for creating interactive and dynamic content on web pages.

2. **What are the data types in JavaScript?**
   - **Answer:** 
     - Primitive: `String`, `Number`, `Boolean`, `Null`, `Undefined`, `Symbol`, `BigInt`.
     - Non-primitive: `Object` (includes `Array`, `Function`, etc.).

3. **What is the difference between `var`, `let`, and `const`?**
   - **Answer:**
     - `var`: Function-scoped, can be redeclared and updated.
     - `let`: Block-scoped, cannot be redeclared.
     - `const`: Block-scoped, cannot be redeclared or reassigned.

4. **What is `undefined` vs. `null`?**
   - **Answer:** 
     - `undefined`: A variable that has been declared but not initialized.
     - `null`: Represents an intentional absence of value.

5. **How does JavaScript handle type coercion?**
   - **Answer:** JavaScript automatically converts types when performing operations:
     ```javascript
     console.log('5' - 3); // 2 (string to number)
     console.log('5' + 3); // "53" (number to string)
     ```

---

### **Intermediate JavaScript Questions**

6. **What are JavaScript closures?**
   - **Answer:** A closure is a function that retains access to its lexical scope, even when executed outside of it.
   ```javascript
   function outer() {
       let count = 0;
       return function inner() {
           count++;
           return count;
       };
   }
   const counter = outer();
   console.log(counter()); // 1
   console.log(counter()); // 2
   ```

7. **Explain `this` in JavaScript.**
   - **Answer:** `this` refers to the context in which a function is executed:
     - In a method, `this` refers to the object.
     - In a function, `this` refers to the global object (`window` in browsers).
     - In `strict mode`, `this` is `undefined` in regular functions.

8. **What is the difference between `==` and `===`?**
   - **Answer:** 
     - `==`: Abstract equality operator, performs type coercion.
     - `===`: Strict equality operator, does not perform type coercion.

9. **What is the purpose of the `bind()`, `call()`, and `apply()` methods?**
   - **Answer:** These methods set the `this` context of a function:
     - `call`: Invokes the function with arguments passed individually.
     - `apply`: Invokes the function with arguments passed as an array.
     - `bind`: Returns a new function with `this` bound to the specified context.

10. **What are arrow functions?**
    - **Answer:** Arrow functions provide a concise syntax for writing functions and do not bind their own `this`.
    ```javascript
    const add = (a, b) => a + b;
    ```

---

### **DOM and Browser Concepts**

11. **What is the DOM?**
    - **Answer:** The Document Object Model is a programming interface that represents the structure of a web page as a tree of objects.

12. **How do you select DOM elements in JavaScript?**
    - **Answer:**
      - `getElementById()`
      - `getElementsByClassName()`
      - `querySelector()`
      - `querySelectorAll()`

13. **What is event delegation?**
    - **Answer:** A technique where a single event listener is added to a parent element to handle events on its children.
    ```javascript
    document.getElementById('parent').addEventListener('click', function(event) {
        if (event.target && event.target.matches('button.class')) {
            console.log('Button clicked');
        }
    });
    ```

14. **What are the different types of events in JavaScript?**
    - **Answer:** Mouse events, Keyboard events, Form events, Window events, etc.

15. **What is the difference between `preventDefault()` and `stopPropagation()`?**
    - **Answer:**
      - `preventDefault()`: Prevents the default behavior of the event.
      - `stopPropagation()`: Stops the event from propagating to parent elements.

---

### **Advanced JavaScript Questions**

16. **What is the difference between synchronous and asynchronous programming?**
    - **Answer:** 
      - Synchronous: Code is executed line by line.
      - Asynchronous: Code execution is non-blocking (e.g., `setTimeout`, Promises).

17. **What are Promises?**
    - **Answer:** Promises are objects representing the eventual completion or failure of an asynchronous operation.
    ```javascript
    const promise = new Promise((resolve, reject) => {
        let success = true;
        success ? resolve('Done') : reject('Error');
    });
    ```

18. **What is async/await?**
    - **Answer:** A syntactic sugar over Promises to handle asynchronous code in a more synchronous manner.
    ```javascript
    async function fetchData() {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
    }
    ```

19. **What is the event loop?**
    - **Answer:** The event loop handles the execution of multiple pieces of code (callbacks, Promises) in a non-blocking way, allowing asynchronous operations in JavaScript.

20. **What are modules in JavaScript?**
    - **Answer:** Modules allow code to be divided into reusable pieces:
      - **ES6 Modules:** `import`/`export`.
      - **CommonJS Modules:** `require`/`module.exports`.


Here are detailed answers for questions **61 to 80** with additional explanations and examples:

---

### **Additional JavaScript Questions (61–80)**

61. **How do you handle errors in JavaScript?**
   - **Answer:** Errors in JavaScript can be handled using `try-catch` blocks or by handling rejections in Promises with `.catch()`.
   ```javascript
   try {
       let result = JSON.parse("invalid JSON");
   } catch (error) {
       console.error("Error occurred:", error.message);
   }
   ```

62. **What are higher-order functions?**
   - **Answer:** A function that takes another function as an argument or returns a function.
   ```javascript
   function higherOrderFunction(fn) {
       return fn(5);
   }
   console.log(higherOrderFunction(x => x * 2)); // 10
   ```

63. **Explain `map()`, `filter()`, and `reduce()`.**
   - **Answer:**
     - `map()`: Transforms each element of an array and returns a new array.
     - `filter()`: Returns a new array containing elements that satisfy a condition.
     - `reduce()`: Reduces an array to a single value using a reducer function.
   ```javascript
   const nums = [1, 2, 3, 4];
   console.log(nums.map(x => x * 2)); // [2, 4, 6, 8]
   console.log(nums.filter(x => x > 2)); // [3, 4]
   console.log(nums.reduce((sum, x) => sum + x, 0)); // 10
   ```

64. **What is hoisting in JavaScript?**
   - **Answer:** Hoisting moves variable and function declarations to the top of their scope before execution. However, initialization is not hoisted.
   ```javascript
   console.log(a); // undefined
   var a = 10; // Declaration is hoisted, but not initialization
   ```

65. **What is the difference between deep copy and shallow copy?**
   - **Answer:**
     - **Shallow Copy:** Copies the first level of the object; nested objects are still referenced.
     - **Deep Copy:** Recursively copies all levels of an object.
   ```javascript
   let obj = { a: 1, b: { c: 2 } };
   let shallowCopy = { ...obj };
   shallowCopy.b.c = 3; // Affects original object
   let deepCopy = JSON.parse(JSON.stringify(obj));
   deepCopy.b.c = 4; // Original object remains unchanged
   ```

66. **What is debouncing and throttling?**
   - **Answer:**
     - **Debouncing:** Delays execution of a function until after a specified time has passed since the last invocation.
     - **Throttling:** Ensures a function is executed at most once in a specified time interval.
   ```javascript
   function debounce(func, delay) {
       let timeout;
       return (...args) => {
           clearTimeout(timeout);
           timeout = setTimeout(() => func(...args), delay);
       };
   }
   ```

67. **What are generators in JavaScript?**
   - **Answer:** Generators are functions that can be paused and resumed, allowing lazy evaluation. They are created using `function*`.
   ```javascript
   function* generateNumbers() {
       yield 1;
       yield 2;
       yield 3;
   }
   const gen = generateNumbers();
   console.log(gen.next().value); // 1
   console.log(gen.next().value); // 2
   ```

68. **Explain the difference between `setTimeout` and `setInterval`.**
   - **Answer:**
     - `setTimeout`: Executes a function once after a specified delay.
     - `setInterval`: Executes a function repeatedly at a specified interval.
   ```javascript
   setTimeout(() => console.log("Runs once after 2 seconds"), 2000);
   setInterval(() => console.log("Runs every 2 seconds"), 2000);
   ```

69. **What are Service Workers in JavaScript?**
   - **Answer:** Service Workers are background scripts that run separately from the main browser thread. They enable features like caching for offline support and push notifications.
   ```javascript
   navigator.serviceWorker.register('/sw.js').then(() => {
       console.log('Service Worker Registered');
   });
   ```

70. **What is WebSocket, and how does it work?**
   - **Answer:** WebSocket is a protocol for full-duplex communication between a client and a server over a single persistent connection.
   ```javascript
   const socket = new WebSocket('ws://example.com');
   socket.onmessage = (event) => console.log(event.data);
   ```

---

### **More Sections**

#### **JavaScript Design Patterns**

71. **What is the Singleton pattern in JavaScript?**
   - **Answer:** Ensures a class has only one instance and provides a global access point to it.
   ```javascript
   const Singleton = (function() {
       let instance;
       function createInstance() {
           return { id: Math.random() };
       }
       return {
           getInstance: () => instance || (instance = createInstance())
       };
   })();
   ```

72. **What is the Module pattern in JavaScript?**
   - **Answer:** Encapsulates code into a module to maintain privacy and organize code.
   ```javascript
   const Module = (function() {
       let privateVar = 'I am private';
       return {
           publicMethod: () => console.log(privateVar)
       };
   })();
   ```

---

#### **Asynchronous JavaScript**

73. **What is the difference between microtasks and macrotasks?**
   - **Answer:** 
     - **Microtasks:** Include Promises and `process.nextTick()`, executed before macrotasks.
     - **Macrotasks:** Include `setTimeout` and `setInterval`.

74. **What is the Fetch API?**
   - **Answer:** A modern way to make HTTP requests, replacing `XMLHttpRequest`.
   ```javascript
   fetch('https://api.example.com/data')
       .then(response => response.json())
       .then(data => console.log(data))
       .catch(error => console.error(error));
   ```

---

#### **JavaScript ES6+ Features**

75. **What are template literals?**
   - **Answer:** Allows multi-line strings and embedded expressions using backticks (`` ` ``).
   ```javascript
   const name = 'John';
   console.log(`Hello, ${name}!`);
   ```

76. **What are rest and spread operators?**
   - **Answer:** 
     - **Rest (`...`)**: Collects arguments into an array.
     - **Spread (`...`)**: Expands an array into individual elements.
   ```javascript
   function sum(...args) {
       return args.reduce((a, b) => a + b, 0);
   }
   console.log(sum(1, 2, 3)); // 6
   ```

---

#### **Event Handling and Advanced DOM**

77. **What is the Shadow DOM?**
   - **Answer:** A scoped DOM tree that encapsulates styles and markup, used in Web Components.

78. **What is the difference between `event.target` and `event.currentTarget`?**
   - **Answer:**
     - `event.target`: The actual element that triggered the event.
     - `event.currentTarget`: The element to which the event listener is attached.

---

#### **Miscellaneous**

79. **What is a WeakMap in JavaScript?**
   - **Answer:** A `WeakMap` is a collection of key-value pairs where keys are objects, and references to these keys are weak.
   ```javascript
   let weakMap = new WeakMap();
   let obj = {};
   weakMap.set(obj, "value");
   ```

80. **What is the difference between `Object.freeze()` and `Object.seal()`?**
   - **Answer:**
     - `Object.freeze()`: Prevents any changes to an object.
     - `Object.seal()`: Prevents adding or removing properties but allows modifying existing ones.
