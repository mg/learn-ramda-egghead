#  Add and Remove Items in Arrays using Filter, Reject and Partition in Ramda
[Video](https://egghead.io/lessons/javascript-ramda-filter-reject-and-partition?pl=learn-ramda-js-ec318ad7)

```js
import { filter, reject, partition } from 'ramda'

const pets = [
  { name: 'Spike', type: 'dog' },
  { name: 'Mittens', type: 'cat' },
  { name: 'Rover', type: 'dog' },
  { name: 'Fluffy', type: 'cat' },
  { name: 'Fido', type: 'dog' },
]

const dogCheck = pet => pet.type == 'dog'

const result1 = filter(dogCheck, pets) // -> list of dogs
const result2 = reject(dogCheck, pets) // -> list of cats
const result2 = partition(dogCheck, pets) // -> array of two lists, one of dogs and one of cats
```
