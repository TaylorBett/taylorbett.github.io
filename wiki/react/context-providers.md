---
layout: page
title: Testing
permalink: /wiki/react/context-providers/
parent:
    text: React
    link: /wiki/react
---

#### TLDR:

Use context providers for data that needs to be accessible by many components and at many levels in a component tree.

Good use cases: visual themes, user data in authenticated area

Wrap top level of required component tree in a Context Provider

```javascript
const ThemeContext = React.createContext({
    baseColor: '#fff',
    highlightColor: '#123456',
});

const ThemeProvider = props => (
  <ThemContext.Provider value="dark">
    {props.children}
  </ThemContext.Provider>
);
```

Use a Context Consumer to wrap the lower component in tree to access the context's data

```javascript
<ThemeContext.Consumer>
  <Button color={baseColor} text="Wow, context API" />
</ThemeContext.Consumer>
```