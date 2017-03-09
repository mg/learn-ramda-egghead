#  Declaratively Map Data Transformations to Object Properties Using Ramda evolve
[Video](https://egghead.io/lessons/javascript-declaratively-map-data-transformations-to-object-properties-using-ramda-evolve?pl=learn-ramda-js-ec318ad7)

When we want to do a simple modification of an object we can use ``merge``. When the modifications become more extensive, ``evolve`` can make these modifications clearer.

```js
import { merge, toUpper, evolve, multiply, inc } from 'ramda'

const product = {
  name: 'cog',
  price: 100,
  details: {
    shippingInfo: {
      weight: 7,
      method: 'ups',
    },
  },
}

const adjustPrice1 = p => merge(p, {name: toUpper(p.name)})
const result1 = adjustPrice1(product) // -> {name: 'COG', price: 100, details: ...}

const adjustPrice2 = evolve({
  name: toUpper,
  price: multiply(2),
  details: {
    shippingInfo: {
      weight: inc,
    },
  }
})

const result2 = adjustPrice2(product) // -> {name: 'COG', price: 200, details: {shippingInfo: {weight: 2, method: 'ups'}} }
```
