# Redux Notes

## createStore

### Methods

* `dispatch`
  - The only way to trigger a state change
  - The store’s reducing function will be called with the current getState() result and the given action synchronously
  - Subscriptions are called after the root reducer has returned the new state, so can call dispatch in subscription listeners
* `subscribe`
  - Add a new change listener
* `getState`
* `replaceReducer`
* `[$$observable]`

### Dependencies

* `lodash/isPlainObject`
* `symbol-observable`

### Notes

* Only one store per app
* The only way to change the data in the store is to call `dispatch()` on it
* The `reducer` creates the next state tree 
* Make sure to return `Object.assign({}, state, newData)` to prevent mutation
* If you use `combineReducers` to produce the root reducer function, the `preloadedState` of `createStore` must be an object with the same shape as `combineReducers` keys

## combineReducers

### Private Methods

* getUndefinedStateErrorMessage
  - 
* getUnexpectedStateShapeWarningMessage
* assertReducerSanity


## applyMiddleware

### Notes

* The only store enhancer (see `createStore`) that ships with Redux
* Applies a middleware to the dispatch method
* Each middleware will be given the `dispatch` and `getState` functions as named arguments

## bindActionCreators

### Notes

* Convenience method, turns object of action creators into object with functions wrapped into a `dispatch` call
* `redux-thunk` is an example of such a middleware

## compose

### Notes

* [reduceRight](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/ReduceRight)

## Data Flow

1. Call `store.dispatch(action)`
2. Return next application state, `reducer(previousState, action)`
3. Root reducer will combine multiple reducers with `combineReducers`
4. Save complete state tree returned by root reducer, register listeners with `store.subscribe(listener)`

## Glossary

### action

### dispatch(er)

### reducer

### state

The single state value that is managed by the store and returned by getState(). It represents the entire state of a Redux application, which is often a deeply nested object. The state should be any type that can is serialisable.

### store 

A store is not a class. It’s just an object with a few methods on it. To create it, pass your root reducing function to createStore.

### store enhancer

## Resources

* [Documentation](http://redux.js.org/)
* [Presentational and Container Components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0#.e9cjtwuam)
* [The Case for Flux](https://medium.com/swlh/the-case-for-flux-379b7d1982c6#.s4iqur39x)
