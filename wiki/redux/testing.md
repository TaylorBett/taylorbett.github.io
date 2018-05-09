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

#### Testing action creators

```javascript
it('should create an action to fetch movies', () => {
    const expectedAction = {
        type: constants.FETCH_MOVIES_REQUEST
    };
    expect(MoviesActions.fetchMoviesRequest()).toEqual(expectedAction);
});
```

#### Testing reducers

Call reducer with previous state and your action, compare expected vs actual output

```javascript
it('should handle ADD_SAVED_PRODUCT action', () => {
    const addProductAction = {
        type: ADD_SAVED_PRODUCT,
        productId: "2"
    };
    expect(searchReducer(initialState, addProductAction)).toEqual({
        "savedProducts": [
            {
                "name": "Product2",
                "id": "2",
            }
        ],
    });
});
```

#### Testing multiple action dispatch flows

- Create iterable array of action objects, ordered as desired
- Iterate through, dispatching them
- Test expected vs actual state after all actions

#### Test initial state

Retrieve initial state via `store.getState()` before dispatching any actions