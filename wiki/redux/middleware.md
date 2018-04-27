---
layout: page
title: Middleware
permalink: /wiki/redux/middleware/
parent:
    text: Redux
    link: /wiki/redux
---

#### TLDR:

3rd party libraries that run between the action dispatch and the reducer in Redux, enabling logging, analytics and other executables to run when actions are dispatched.

#### Usage

- Composable into a chain of multiple middleware instances

##### Thunk
- Action creators return a function instead of an action
- You can delay calling the action function or call the function conditionally etc.

##### Sagas
- For async data fetching + other side effects of actions
- Better for testing
- More efficient
- Easier to manage
- Uses generators

