# Notes on JavaScript concepts

## Table of Contents

1. **[this keyword](#1-this-keyword)**
2. **[call, apply, bind](#2-call-apply-bind)**

---

## 1. this

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

## 2. call, apply, bind

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
