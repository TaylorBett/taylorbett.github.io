---
layout: page
title: Default parameter values
permalink: /wiki/javascript/default-parameter-values
parent:
    text: Javascript
    link: /wiki/javascript
---

#### TLDR:

Provide a default value to a function, used in the case of no param provided or `undefined` value provided.

#### Usage

```javascript
function myFunc = (x = 10) => {
    return x;
}
```

#### Behaviour

Default value is used when the parameter is not given or an `undefined` value is given for the parameter.

Providing a `null` value will NOT use the default, it will use the provided `null` value.