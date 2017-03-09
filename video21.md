#  Debug Function Compositions with Ramda's Tap Function
[Video](https://egghead.io/lessons/javascript-debug-function-compositions-with-ramda-s-tap-function?pl=learn-ramda-js-ec318ad7)

``tap()`` creates side-effects without interrupting the flow of composition, much like **RxJS**'s ``do()`` operator.

```js
import { identity, compose, fromPairs, map, split, tail, tap } from 'ramda'

const queryString = '?page=2&pageSize=10&total=203'

const parseQs = compose(
  fromPairs,
  map(split('=')),
  tap(console.log),
  split('&'),
  tail,
)
```
