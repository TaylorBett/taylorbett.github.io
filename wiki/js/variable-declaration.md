---
layout: page
title: Variable declaration
permalink: /wiki/javascript/variable-declaration
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR:

`const` Not reassignable, block scope

`let` Reassignable, block scope

`var` Reassignable, function scope

#### Tabulated data

| Type          | Scope    | Reassignable  | Mutable     | Hoisted      | Temporal dead zone |
| ------------- |----------|---------------|
| `const`       | Block    | No            | Yes *       | Yes          | Yes                |
| `let`         | Block    | Yes           | Yes         | Yes          | Yes                |
| `var`         | Function | Yes           | Yes         | Yes          | No                 |


Note: `const` are mutable in that arrays and objects can be mutated, since this is not a reassignment.

#### Hoisting

In JS, variable declarations are 'hoisted' to the top of their scope on execution. This means that in written code, one can reference a variable (in relevant scope) that has not yet been declared.

Applies to all, var, let and const.

*But*, referencing `let` and `const` before assignment will cause a reference error, so in practice it does not feel like typical `var` hoisting.

```javascript
console.log(myVar); // ok
var myVar = 2;
```

```javascript
console.log(myVar); // raises a ReferenceError !
let myVar = 2;
```

This is called 

#### Temporal dead zone

When a reference error appears due to referencing a `let` or `const` before assignment, even though the declaration has in fact been hoisted.

