#  Handle Errors in Ramda Pipelines with tryCatch
[Video](https://egghead.io/lessons/javascript-handle-errors-in-ramda-pipelines-with-trycatch?pl=learn-ramda-js-ec318ad7)

- ``tryCatch(tryFn, catchFn)``: call **tryFn** and return its value. If it throws, call **catchFn** and return its value.

- ``propOr(defaultValue, propName)``: short-hand for using **tryCatch** with **prop**.

```js
import { prop, pipe, toUpper, tryCatch, always, propOr } from 'ramda'

const person = {
  name: 'Sally Jones',
}

const getName = tryCatch(prop('name'), always('Default'))
const getName2 = propOr('Default', 'name')
const getUpperName = pipe(getName, toUpper)
const result1 = getUpperName(person) // -> 'SALLY JONES'
const result2 = getUpperName(undefined) // -> 'DEFAULT'
```
