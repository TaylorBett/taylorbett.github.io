---
layout: page
title: Generators
permalink: /wiki/javascript/generators/
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR:

A function that saves internal context for repeated use, updating context each call.

#### Usage

```javascript
function * idMaker = () => {
    var index = 0;
    while (index < 2) {
        yield index;
        index = index + 1;
    }
}

var gen = idMaker();

gen.next().value; // 0
gen.next().value; // 1
gen.next().value; // undefined
```

#### Behaviour

- Returns an iterable object
- Can call `gen.next().value` to run the  function to the next `yield`, returning the value and updating the internal context

#### Advanced usage

The yield* expression enables a generator to call another generator function during iteration.

```javascript
// Yield * Example
function * genB(i) {
    yield i + 1;
    yield i + 2;
    yield i + 3;
}

function * genA(i) {
    yield i;
    yield* genB(i);
    yield i + 10;
}

var gen = genA(10);

gen.next().value; // 10
gen.next().value; // 11
gen.next().value; // 12
gen.next().value; // 13
gen.next().value; // 20
```

The returned object also contains a property showing if the iterator is 'done' or not (reached a return statement), no more accessible yields

```javascript
// Generator Return Example
function* yieldAndReturn() {
  yield "Y";
  return "R";
  yield "unreachable";
}

var gen = yieldAndReturn()
gen.next(); // { value: "Y", done: false }
gen.next(); // { value: "R", done: true }
gen.next(); // { value: undefined, done: true }
```