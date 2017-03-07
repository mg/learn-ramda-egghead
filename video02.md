# Eliminate Function Arguments (Point-Free Style) with Ramda's Converge
[Video](https://egghead.io/lessons/javascript-eliminate-function-arguments-point-free-style-with-ramda-s-converge?pl=learn-ramda-js-ec318ad7)

When we see the same argument mention twice in a function, it is a sign to bring in ``converge`` to make the function **point free**.

```js
import { converge, equals, head, sort, descend, identity, compose } from 'ramda'

const shouldBeTrue = [6, 3, 4, 5 ,2, 1]
const shouldBeFalse = [3, 4, 5, 3, 1]

// xs converges on equals
const isFirstBiggest = xs =>
  xs[0] === xs.sort((a, b) => b - a)[0]

const biggestItem = compose(head, sort(descend(identity)))
const isFirstBiggestPf = converge(
  equals, [ head, biggestItem ]
)

console.log(isFirstBiggest(shouldBeTrue))  // true
console.log(isFirstBiggest(shouldBeFalse)) // false
```
