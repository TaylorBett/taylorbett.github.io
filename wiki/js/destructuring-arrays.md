---
layout: page
title: Destructuring arrays
permalink: /wiki/javascript/destructuring-arrays/
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR

Nicer syntax for creating new variables from data extracted from an array. 

Useful if you have known values at consistent positions in an array.

### Standard usage

```javascript
const myArray = ["a", "b", "c"];
```

#### Without destructuring

```javascript
const x = myArray[0];
const y = myArray[1];
```

#### With destructuring

```javascript
const [x, y] = myArray; // Concise

console.log(x) // "a"
console.log(y) // "b"
```