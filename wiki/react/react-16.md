---
layout: page
title: React 16 - What's new
permalink: /wiki/react/react-16/
parent:
    text: React
    link: /wiki/react
---

#### Render multiple elements without wrapping them:

- Function and class components can return an array of elements and can be included inside other components
- Can also create a proxy function which takes props and returns props.children, then wrap elements in this, removing the need for the array

#### Render text-only components

- Return just plain text from components, no need to wrap them in containing elements any more

#### Using portals (mostly for modals)

- `ReactDom.ceatePortal(new subtree, target container)`
- Can use this to render elements outside of the current DOM/component tree
- Handy for modals/overlays

#### Define DOM attributes

- Can now add custom attributes
- Needs a string, object or number (all converted to string)
- Will *NOT* take a bool, function or symbol

#### Call setState with null to avoid triggering an update

- Return null inside a setState to avoid an update

#### Fragments

- `<React.Fragment>` or `<></>` as sugar, avoids creating unnecessary containing divs

#### Create Dom References

- Use React.createRef();
- Pass this reference to an element in render, and to other libraries wanting a node ref
- Useful for d3.js

#### getDerivedStateFromProps

- getDerivedStateFromProps(nextProps, prevState)
- called on first mount and when receiving new props
- Use this to return mutated state conditionally

#### Capture values using getSnapshotBeforeUpdate

- getSnapshotBeforeUpdate(prevProps, prevState)
- Use this to get a snapshot of the component state BEFORE it updates
- Snapshot is accessible in componentDidUpdate as 3rd parameter
- Example usage: chat app, check scroll position on update, if at the bottom then update scroll position to stay there, else do nothing

