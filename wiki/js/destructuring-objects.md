---
layout: page
title: Destructuring objects
permalink: /wiki/javascript/destructuring-objects/
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR

Convenient sugar for creating new variables by extracting values from objects.

### Standard usage

Allows for destructuring objects on one line, very concise and convenient.

Let's consider the following object for all the samples:

```javascript
const person = {
  firstName: "Nick",
  lastName: "Anderson",
  age: 35,
  sex: "M"
}
```

#### Without destructuring

```javascript
const first = person.firstName;
const age = person.age;
const city = person.city || "Paris";
```

#### With destructuring

```javascript
const { firstName: first, age, city = "Paris" } = person; // That's it !

console.log(age) // 35 -- A new variable age is created and is equal to person.age
console.log(first) // "Nick" -- A new variable first is created and is equal to person.firstName
console.log(firstName) // ReferenceError -- person.firstName exists BUT the new variable created is named first
console.log(city) // "Paris" -- A new variable city is created and since person.city is undefined, it uses the default value provided, "Paris"
```

### Function parameters

#### Without destructuring

```javascript
function joinFirstLastName(person) {
  const firstName = person.firstName;
  const lastName = person.lastName;
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```

#### With destructuring

In destructuring the object parameter person, we get a more concise function:

```javascript
const joinFirstLastName = ({ firstName, lastName }) => firstName + '-' + lastName;

joinFirstLastName(person);
```