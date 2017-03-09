#  Get a List of Unique Values From Nested Arrays with Ramda
[Video](https://egghead.io/lessons/javascript-get-a-list-of-unique-values-from-nested-arrays-with-ramda?pl=learn-ramda-js-ec318ad7)

The goal is to get a unique list of color values available for the product independent of what sizes each color belongs to.

```js
import { prop, compose, pluck, chain, uniq, unnest } from 'ramda'

const product = {
  name: "Sample Data",
  sizes: [
    {
      name: "L",
      colors: [
        {
          name: "Red"
        },
        {
          name: "Blue"
        }
      ]
    },
    {
      name: "M",
      colors: [
        {
          name: "Green"
        },
        {
          name: "Yellow"
        }
      ]
    },
    {
      name: "S",
      colors: [
        {
          name: "Orange"
        },
        {
          name: "Purple"
        },
        {
          name: "Blue"
        }
      ]
    }
  ]
}

const getSizes = prop('sizes')
const sizes = getSizes(product)

const getColors = map(prop('colors'))
const colors = getColors(sizes) // -> [ [ {name: 'Red'}, {name: 'Blue'}], [{name: 'Green'}, {name: 'Yellow'}], [...] ]

const getColorNames = map(pluck('name'))
const colorNames = getColorNames(colors) // -> [ ['Red', 'Blue'], ['Green', 'Yellow'], ['Orange', 'Purple', 'Blue'] ]

// since the map in getColors is what creates the nested array, we can use unnest or chain to remove it
const getColors2 = compose(unnest, map(prop('colors')))
const getColors3 = chain(prop('colors'))
const getColorNames2 = pluck('name')


// compose it
const getUniqueColors(compose(uniq, getColorNames2, getColors3, getSizes)) // -> ['Red', 'Blue', 'Green', 'Yellow', 'Orange', 'Purple']
const uniqueColors = getUniqueColors(product)
```
