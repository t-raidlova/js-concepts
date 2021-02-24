# Notes on JavaScript concepts

## Table of Contents

1. **[This keyword](#1-this-keyword)**
2. **[Call, apply, bind](#2-call-apply-bind)**
3. **[Closures](#3-Closures)**

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

## 3. Closures

- Closure is when a function remembers its lexical scope even when the function is executed outside that lexical scope
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
