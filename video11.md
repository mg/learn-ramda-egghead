#  Curry and Uncurry Functions with Ramda
[Video](https://egghead.io/lessons/javascript-curry-and-uncurry-functions-with-ramda?pl=learn-ramda-js-ec318ad7)

If we use ``curry()`` to create a curried function, we can both call it in a curried form and a non-curried form.

```js
import { curry, curryN, uncurryN } from 'ramda'

const add1 = (a, b) => a + b
const result1 = add(1,2) // -> 3

const add2 = a => b => a + b // manually curried function
const inc1 = add2(1)
const result2 = inc1(2) // -> 3
const result3 = add2(1)(2) // -> 3, cannot call a manually curried function in a non-curried way

const add3 = curry(add1)
const inc2 = add3(1)
const result4 = inc2(2) // -> 3, curried
const result5 = add3(1, 2) // -> 3, non-curried

// currying a manually curried function
const multi = a => b => a * b
const multiply = uncurryN(2, multi)
const result6 = multiply(2,4) // -> 6
```
