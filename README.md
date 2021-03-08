# Notes on JavaScript concepts

## Table of Contents

1. **[This keyword](#1-this-keyword)**
2. **[Call, apply, bind](#2-call-apply-bind)**
3. **[HOF](#3-HOF)**
4. **[Closures](#4-Closures)**

---

## 1. This

- refers to what object is it inside of - what is the object environment
- gives methods access to their object
- is **dynamically** scoped - it doesn't matter where it was written, but **how** the function was called

```javascript
const obj = {
  name: "Grimes",
  sing: function () {
    console.log(this); // method on an object, use regular function
    var anotherFunc = function () {
      console.log(this); // this points to the window! use arrow function here instead
    };
  },
};
```

- if the function is defined as an arrow function, the value of this is always the same as this in the parent scope
- with arrow functions, the value of this can't be changed with call, apply or bind

## 2. Call, apply, bind

- → ways to call a function (sets the this keyword) with different context
- difference between call() and apply() is that call() passes all arguments after the first one on to the invoked function, while apply() takes an array as its second argument

```javascript
someFunc.call(thisArg, 1, 2, 3);
someFunc.apply(thisArg, [1, 2, 3]);
```

- bind() returns a copy of the bound function with new context
- call() executes the bound function **immediately**

```javascript
const person = { name: "Tereza" };

function sayHi(age) {
  return `${this.name} is ${age}`;
}

console.log(sayHi.call(person, 21));
console.log(sayHi.bind(person, 21));

// output: Tereza is 21 function
```

## 3. HOF

- in JavaScript, functions are first class objects
- this means functions can be assigned to an array or an object or they can be passed into another function
- Higher-Order-Function is a function that takes a function as an argument and returns a function

```javascript
function manipulateArray(numbers, instructions) {
  const newArr = [];

  for (number of numbers) {
    newArr.push(instructions(number));
  }
  return newArr;
}

const multiplyBy2 = (input) => input * 2;
const result = manipulateArray([1, 2, 3], multiplyBy2);
```

```javascript
function manipulateArray(numbers, instructions) {
  const newArr = [];

  for (let i = 0; i < numbers.length; i++) {
    newArr.push(instructions(numbers[i]));
  }
  return newArr;
}
```

## 4. Closures

- closure is when a function remembers its lexical scope even when the function is executed outside that lexical scope
- → functions remember their creation environment and can reference independent variables within that environment
- enable function factories
- enable private data
- memory efficient
- encapsulation

```javascript
function makeFunc() {
  let name = "Tereza";
  function displayName() {
    alert(name);
  }
  return displayName;
}

var myFunc = makeFunc();
myFunc();
```

- The instance of displayName maintains a reference to its lexical environment, within which the variable name exists. For this reason, when myFunc is invoked, the variable name remains available for use
