# Convert a QueryString to an Object using Function Composition in Ramda
[Video](https://egghead.io/lessons/javascript-convert-a-querystring-to-an-object-using-function-composition-in-ramda?pl=learn-ramda-js-ec318ad7)

```js
import { compose, fromPairs, map, split, tail } from 'ramda'

const queryString = '?page=2&pageSize=10&total=203'
/*
  use tail to get rid of ?, tail returns all but first element: 'page=2&pageSize=10&total=203'
  use split('&') top tokenize string based on & character and return an array :['page=2', 'pageSize=10', 'total=203']
  use map and split on equal sign to parse name value pair, we get array of array's: [['page', '2'], ['pageSize', '10'], ['total', '203']]
  use fromPairs to construct a new object from an array of arrays, where each sub array contains two items, name and value: {page: '2', pageSize: '10', total: '203'}
*/
const parseQs = compose(fromPairs, map(split('=')), split('&'), tail)

console.log(parseQs(queryString))
```
