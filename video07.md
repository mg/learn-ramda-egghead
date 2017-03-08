#  Change Object Properties with Ramda Lenses
[Video](https://egghead.io/lessons/javascript-change-object-properties-with-ramda-lenses?pl=learn-ramda-js-ec318ad7)

- ``lens(getterFn, setterFn)``: Construct a lens with a **getter** function and a **setter** function.

- ``view(lens) -> object -> value``: Construct a view lens that executes the **lenses** **getter** function when supplied an object. Returns the result of the **setter**.

- ``set(lens, value) -> object -> object``: Construct a set lens that executes the **lenses** **setter** function with value **value** when supplied an object. Returns a modified object.

- ``lensProp(name)``: Shorthand for ``lens(prop(NAME), assoc(NAME))``.

- ``over(lens)``: Run a function over an object with the focus of the lens.

```js
import { lens, prop, assoc, lensProp, view, set, over, toUpper } from 'ramda'

const person = {
  firstName: 'Fred',
  lastName: 'Flintstone',
}

//const fLens = lens(prop('firstName'), assoc('firstName'))
const fLens = lensProp('firstName')
const result1 = view(fLens, person) // -> 'Fred'
const result2 = set(fLens, 'Wilma', person) // -> {firstName: 'Wilma', lastName: 'Flintstone'}
const result3 = over(fLens, toUpper, person) // -> {firstName: 'FRED', lastName: 'Flintstone'}
```
