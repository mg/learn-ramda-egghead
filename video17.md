#  Sort an Array of Objects by Multiple Fields with Ramda's sortWith
[Video](https://egghead.io/lessons/javascript-sort-an-array-of-objects-by-multiple-fields-with-ramda-s-sortwith?pl=learn-ramda-js-ec318ad7)

```js
import { prop, sort, sortWith, ascend, descend } from 'ramda'

const sample = [
  { name: "Sally", age: 29, height: 65 },
  { name: "Zac", age: 29, height: 72 },
  { name: "John", age: 32, height: 61 },
  { name: "Lisa", age: 28, height: 63 },
  { name: "Bob", age: 29, height: 66 },
  { name: "Allen", age: 29, height: 66 },
]

const result1 = sort(ascend(prop('age')), sample) // sort by age ascending

const result2 = sortWith([
    ascend(prop('age')), // sort by age descending
    descend(prop('height')), // then sort by height ascending
    ascend(prop('name')), // lastly, sort by name alphabetically
  ],
  sample,
)
```
