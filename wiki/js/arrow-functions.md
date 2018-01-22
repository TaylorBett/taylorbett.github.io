---
layout: page
title: Arrow functions
permalink: /wiki/javascript/arrow-functions/
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR

- More concise
- Implicit return
- `this` picked up from context

#### Implicit return

No need to specify a return for simple functions, it is already there implicitly.

```javascript
const double = (x) => x * 2;
console.log(double(2)); // 4
```

#### this from context

`this` is immediately picked up from the parent/usage context, eliminating old need to use old this assignment trick. 

No more

```javascript
this.myVar = 0;
var that = this;
function() {
    that.myVar++;
}
```

Now

```javascript
this.myVar = 0;
() => {
  this.myVar ++;  
}
```

#### Extra

Note: No need to use brackets if only one argument. 

```javascript
const double = x => x * 2;
```