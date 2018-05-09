---
layout: page
title: Testing
permalink: /wiki/react/testing/
parent:
    text: React
    link: /wiki/react
---

#### TLDR:

Testing patterns with Jest + Enzyme

#### Basic usage

```javascript
describe('My test', () => {
    it('should do my expected behaviour', () => {
        const expected = true;
        const actual = myFunc(myParam);
        expect(actual).toEqual(expected);
    });
});
```

Good practice: Create a function that returns clean state/expected value, re-use this in each test to ensure a sanitary/reset state at the start of each test

#### Shallow Rendering

- Renders the given component *one level deep*.
- Can access and test properties on this result as an object
- OR can see the JSX output with `.getRendererOutput()`

```javascript
import TestUtils from 'react-addons-test-utils';
import MyComponent from './MyComponent';


describe('My test', () => {
    it('should have the right classname', () => {
        const myRenderer = TestUtils.createRenderer();
        const myRender = myRenderer.render(MyComponent);
        expect(myRender.getRenderOutput().props.className).toEqual('my-component');
    });

    it('should be an anchor tag', () => {
        const myRenderer = TestUtils.createRenderer();
        const myRender = myRenderer.render(MyComponent);
        expect(myRender.getRenderOutput().type).toEqual('a');
    });
});
```