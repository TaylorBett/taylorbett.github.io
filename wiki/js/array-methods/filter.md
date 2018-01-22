---
layout: page
title: Array.filter()
permalink: /wiki/javascript/array-methods/filter/
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR

Takes an array, tests each element against a provided function and returns a *new* array of the elements that passed the test.


#### Usage

```javascript
const words = ["spray", "limit", "elite", "exuberant", "destruction", "present", "happy"];

let longWords = words.filter(word => word.length > 6); // ["exuberant", "destruction", "present"]
```


The callback function is invoked with three arguments:

1. the value of the element
2. the index of the element
3. the Array object being traversed

These are accessible inside your callback function, should you need to use them.

```javascript
const words = ["spray", "limit", "elite", "exuberant", "destruction", "destruction", "present", "happy"];

let longWords = words.filter((word, n, arr) => {
    return (word.length > 6 && word === arr[n + 1]);
}); // ["destruction"]
```

Note: Array.filter() does NOT mutate the array on which it was called.

#### Advanced

Array.filter() also takes an optional second argument, the `thisArg`, which allows you to pass in a value to use as `this` when executing the callback.