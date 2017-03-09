#  Convert Object Methods into Composable Functions with Ramda
[Video](https://egghead.io/lessons/javascript-convert-object-methods-into-composable-functions-with-ramda?pl=learn-ramda-js-ec318ad7)

- ``invoker(N, fn)``: **fn** is the name of the object method to invoke and it takes **N** arguments.

- ``constructN(N, constructor)``: Run the **constructor** to construct a object. The **constructor** expects **N** arguments.

```js
// jQuery code
$('#sample')
  .animate(left: '250px')
  .animate(left: '10px')
  .slideUp()

// ramda code to construct and run the jQuery code
import { invoker, compose, constructN } from 'ramda'

const animate = invoker(1, 'animate')
const slide = invoker(0, 'slideUp')
const jq = constructN(1, $)

const animateDiv = compose(
  slide,
  animate(left: '10px'),
  animate(left: '250px'),
  jq,
)

animateDiv('#sample')
```
