#  Pick and Omit Properties from Objects Using Ramda
[Video](https://egghead.io/lessons/javascript-pick-and-omit-properties-from-objects-using-ramda?pl=learn-ramda-js-ec318ad7)

- ``pick([propNames])``: Return a shallow copy of object with only **propNames** and only if those properties are present.

- ``pickAll([propNames])``: Return a shallow copy of object with only **propNames**, undefined value for those properties that are not present.

- ``pickBy(predicateFun: (value, key) => boolean)``: Return a shallow copy of object with only properties where predicate is true.

- ``omit([propNames])``: Return a shallow copy of object with all properties except **propNames**.

```js
import { pick, pickAll, pickBy, contains } from 'ramda'

const product = {
  name: 'widget',
  price: 10,
  avgRating: 4.5,
  shippingWeight: '2 lbs',
  shippingCost: 2
}

const getProps = pick(['name', 'price', 'category'])
const getPropsAll = pickAll(['name', 'price', 'category'])
const getPropsBy = pickBy(val => Number(val))
const getPropsBy2 = pickBy((val, key) => contains('shipping', key))
const getProps2 = omit(['shippingWeight', 'shippingCost'])
const getPropsBy3 = pickBy((val, key) => !contains('shipping', key))

const result1 = getProps(product) // -> {name: 'widget', price: 10}
const result2 = getPropsAll(product) // -> {name: 'widget', price: 10, category: undefined}
const result3 = getPropsBy(product) // -> {price: 10, avgRating: 4.5}
const result4 = getPropsBy2(product) // -> {shippingWeight: '2 lbs', shippingCost: 2}
const result5 = getProps2(product) // -> {name: 'widget', price: 10, avgRating: 4.5}
const result6 = getPropsBy3(product) // -> {name: 'widget', price: 10, avgRating: 4.5}
```
