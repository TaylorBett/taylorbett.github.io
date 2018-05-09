---
layout: page
title: Styled Components
permalink: /wiki/react/styled-components/
parent:
    text: React
    link: /wiki/react
---

#### TLDR:

[Docs](https://www.styled-components.com/docs/)
Style components inside their relevant JS with props-based variants.

#### Props-based variants

```javascript
const Button = styled.button`
  border-radius: 3px;
  padding: 0.25em 1em;
  margin: 0 1em;
  background: transparent;
  color: palevioletred;
  border: 2px solid palevioletred;

  ${props => props.primary && css`
    background: palevioletred;
    color: white;
  `}
`;
```

#### Extend components to add variants

Inherits all of the base component's styles and allows for overrides or extra styles as a variant on that component

```javascript
const ButtonVariant = Button.extend`
/* css here */
`;
```
