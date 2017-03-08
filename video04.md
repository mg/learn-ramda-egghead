# Select a Subset of Properties from a Collection of Objects in Ramda
[Video](https://egghead.io/lessons/javascript-select-a-subset-of-properties-from-a-collection-of-objects-in-ramda?pl=learn-ramda-js-ec318ad7)

```js
import { map, pick, project } from 'ramda'

const products = [
  { name: 'Jeans', price:80, category: 'clothes' },
  { name: 'Hoodie', price:60, category: 'clothes' },
  { name: 'Jacket', price:120, category: 'clothes' },
  { name: 'Cards', price: 35, category: 'games' },
  { name: 'iPhone', price: 649, category: 'electronics' },
  { name: 'Sauce Pan', price: 100, category: 'housewares' },
]

console.log(products.map(product => ({name: product.name, price: product.price})))

const getNameAndPrice = project(['name', 'price']) // same as map(pick(['name', 'price']))
const result = getNameAndPrice(products)

console.log(result)
```
