#  Handle Branching Logic with Ramda's Conditional Functions
[Video](https://egghead.io/lessons/javascript-handle-branching-logic-with-ramda-s-conditional-functions?pl=learn-ramda-js-ec318ad7)

- ``ifElse(predicateFn, trueMapFn, falseMapFn)``: Basic two way branching, run either mapping function based on what predication function returns.

- ``when(predicateFn, trueMapFn)``: Special case two way branching when we want false to return unchanged results

- ``unless(predicateFn, falseMapFn)``: Special case two way branching when we want true to return unchanged results

- ``cond([[predicateFn, falseMapFn], ...])``: N-way branching.

```js
import { lensProp, curry, over, map, ifElse, propEq, identity, when, cond, T } from 'ramda'

const products = [
  { name: 'Jeans', price:80, category: 'clothes' },
  { name: 'Hoodie', price:60, category: 'clothes' },
  { name: 'Jacket', price:120, category: 'clothes' },
  { name: 'Cards', price: 35, category: 'games' },
  { name: 'iPhone', price: 649, category: 'electronics' },
  { name: 'Sauce Pan', price: 100, category: 'housewares' },
]

const priceLens = lensProp('price')

// curry returns a function that accepts a percent value and returns a function that accepts amt value
// perc => amt => discount
const applyDiscount = curry((perc, amt) => amt - (amt * (perc / 100)))

// apply 50% discount on all items
const adjustPrice = over(priceLens, applyDiscount(50))

// if category is clothes, apply 50% discount, else 10% discount
const adjustPrice2 = ifElse(
  propEq('category', 'clothes'), // predicate function
  over(priceLens, applyDiscount(50)), // run if true
  over(priceLens, applyDiscount(10)), // run if false
)

// if category is clothes, apply 50% discount, else no discount
const adjustPrice3 = ifElse(
  propEq('category', 'clothes'),
  over(priceLens, applyDiscount(50)),
  identity,
)

// same as ifElse with identity as false function, i.e. only run mapping function WHEN predicate is true
const adjustPrice4 = when(
  propEq('category', 'clothes'),
  over(priceLens, applyDiscount(50)),
)

// check for 3 categories for different discounts, and no discount on anything else.
const adjustPrice5 = cond([
  [ propEq('category', 'clothes'), over(priceLens, applyDiscount(50)) ],
  [ propEq('category', 'electronics'), over(priceLens, applyDiscount(10)) ],
  [ propEq('category', 'books'), over(priceLens, applyDiscount(90)) ],
  [ T, identity], // default case, only get here if others don't catch it. T is a function that returns true
])

const result = map(adjustPrice, products)

console.log(result)
```
