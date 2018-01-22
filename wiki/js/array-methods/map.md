---
layout: page
title: Array.map()
permalink: /wiki/javascript/array-methods/map/
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR

Takes an array, performs a function on every element in given array and returns a *new* array with the transformed elements.

#### Usage

```javascript
const myArray = [1, 4, 9, 16];

let myMap = myArray.map(x => x * 2); // Array [2, 8, 18, 32]
```

Note: If you do not need to return a new array and just want to do a loop that has side effects, you might just want to use a for / forEach loop instead of a map.

#### Advanced

Array.map() also takes an optional second argument, the `thisArg`, which allows you to pass in a value to use as `this` when executing the callback.