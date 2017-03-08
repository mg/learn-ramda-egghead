#  Declaratively Map Predicates to Object Properties Using Ramda where
[Video](https://egghead.io/lessons/javascript-declaratively-map-predicates-to-object-properties-using-ramda-where?pl=learn-ramda-js-ec318ad7)

##### pluck vs pick vs lens
- ``pluck(name)``: Pluck value in property **name** from object and return.

- ``pick([name])``: Return a copy of object that only contains property **name**.

- ``lensProp(name)``: Provide a lens into property **name** in object that can be used to modify property value.

```js
import { where, equals, lt, __, pipe, filter, pluck } from 'ramda'

const products = [
  { name: 'Jeans', price:80, category: 'clothes' },
  { name: 'Hoodie', price:60, category: 'clothes' },
  { name: 'Jacket', price:120, category: 'clothes' },
  { name: 'Cards', price: 35, category: 'games' },
  { name: 'iPhone', price: 649, category: 'electronics' },
  { name: 'Sauce Pan', price: 100, category: 'housewares' },
]

// const predicate = prod => prod.category === 'clothes' && product.price < 70
const predicate = where({
  category: equals('clothes'),
  price: lt(__, 70), // could use gte(70) for same result
})

const getResults = pipe(filter(predicate), pluck('name'))
const result = getResults(products)

console.log(result)
```
