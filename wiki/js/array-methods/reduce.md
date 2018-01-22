---
layout: page
title: Array.reduce()
permalink: /wiki/javascript/array-methods/reduce/
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR

Takes an array of values and aggregates them into a single returned value.

#### Usage

```javascript
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer)); // 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5)); // 15
```
```javascript
arr.reduce(callback, initialValue);
```

#### callback 

The callback function takes 4 possible arguments:

1. accumulator (required)
The accumulator accumulates the callback's return values; it is the accumulated value previously returned in the last invocation of the callback, or initialValue, if supplied.
2. currentValue (required)
The current element being processed in the array.
3. currentIndex (optional)
The index of the current element being processed in the array. Starts at index 0, if an initialValue is provided, and at index 1 otherwise.
4. array (optional)
The array reduce() was called upon.

#### initialValue (Optional)
Value to use as the first argument to the first call of the callback. If no initial value is supplied, the first element in the array will be used.

NOTE: Calling reduce() on an empty array without an initial value is an error.