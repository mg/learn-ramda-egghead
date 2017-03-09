#  Create an Array From a Seed Value with Ramda's unfold
[Video](https://egghead.io/lessons/javascript-create-an-array-from-a-seed-value-with-ramda-s-unfold?pl=learn-ramda-js-ec318ad7)

```js
import { unfold, curry } from 'ramda'

const throughNByOne = curry((limit, n) => n > limit ? false : [n, n+1])
const result1 = unfold(throughNByOne(20), 1) // -> [1, 2, 3, 4, ... , 20]

const throughNBaseTwo = curry((limit, n) => n > limit ? false : [n, n*1])
const result2 = unfold(throughNBaseTwo(256), 2) // -> [2, 4, 8, 16, ..., 256]
```
