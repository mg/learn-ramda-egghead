#  Refactor to a Point Free Function with Ramda's useWith Function
[Video](https://egghead.io/lessons/javascript-refactor-to-a-point-free-function-with-ramda-s-usewith-function?pl=learn-ramda-js-ec318ad7)

- If ``useWith()`` does not find a transformation function for a parameter, it will automatically default to the ``identity`` function.

```js
import { find, propEq, useWith, identity } from 'ramda'

const countries = [
  {cc: 'GB', flag: '🇬🇧'},
  {cc: 'US', flag: '🇺🇸'},
  {cc: 'CA', flag: '🇨🇦'},
  {cc: 'FR', flag: '🇫🇷'}
]

const getCountry = (cc, list) => find(propEq('cc', cc), list)
const getCountryPF1 = useWith(find, [propEq('cc'), identity])
const getCountryPF2 = useWith(find, [propEq('cc')]) // useWith defaults to identity for list parameter

const results = getCountryPF1('US', countries)
```
