# redux_notes

## createStore

### Methods

* `dispatch`
* `subscribe`
* `getState`
* `replaceReducer`
* `[$$observable]`

### Dependencies

* `lodash/isPlainObject`
* `symbol-observable`

### Notes

* The only way to change the data in the store is to call `dispatch()` on it
* The `reducer` creates the next state tree 
* If you use `combineReducers` to produce the root reducer function, the `preloadedState` of `createStore` must be an object with the same shape as `combineReducers` keys

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

## Glossary

### store enhancer
