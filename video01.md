# Refactor to Point Free Functions with Ramda using compose and converge
[Video](https://egghead.io/lessons/javascript-refactor-to-point-free-functions-with-ramda-using-compose-and-converge?pl=learn-ramda-js-ec318ad7)

Point Free Function is a function that doesn't explicitly mention it's arguments.

```js
import R from 'ramda'

const person = {
  id: 1,
  name: 'Joe',
}

// problem 1: if id is undefined, we should get a default image, not undefined image
const generateUrl = id => `https://img.socialnetwork.com/avatar/${id}.png`

const getUpdatePerson = person => {
  const url = generateUrl(person.id)
  return R.assoc('avatar', url, person) // same as Object.assign()
}

// a function that solves problem 1
const getUrlFromPerson = R.compose(generateUrl, R.propOr('default', 'id'))
const getUpdatePerson2 = person => {
  // person -> R.propOrId(person) -> generateUrl() -> url result
  const url = getUrlFromPerson(person)
  return R.assoc('avatar', url, person) // same as Object.assign()
  // still we are referencing person twice inside this function, will use R.converge to fix
}

// getUpdatePerson as a Point Free Function, person is never named
const getUpdatePerson3 = R.converge(R.assoc('avatar'), [getUrlFromPerson, R.identity])

const result = getUpdatedPerson3(person)
console.log(result)
```
