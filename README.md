# Notes on JavaScript concepts

## Table of Contents

1. **[This keyword](#1-this-keyword)**
2. **[call, apply, bind](#2-call-apply-bind)**

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
      console.log(this); // this points to the window! use arrow function here instead!
    };
  },
};
```

## 2. call, apply, bind
