#  Build a Functional Pipeline with Ramda.js
[Video](https://egghead.io/lessons/javascript-build-a-functional-pipeline-with-ramda-js?pl=learn-ramda-js-ec318ad7)

```js
import { pipe, sort, head, prop } from 'ramda'

const teams = [
  {name: 'Lions', score: 5 },
  {name: 'Tigers', score: 4 },
  {name: 'Bears', score: 6 },
  {name: 'Monkeys', score: 2 },
]

const getTopNameNativeJS = teams => {
  const sorted = teams.sort((a, b) => b.score - a.score) // sort teams in descending order
  const topTeam = sorted[0] // return first item in list
  const topName = topTeam.name // return 'Bears'
  return topName
}

const getTopNameRamda = teams => {
  const sorted = sort((a, b) => b.score - a.score, teams) // sort teams in descending order
  const topTeam = head(sorted) // return first item in list
  const topName = prop('name', topTeam) // return 'Bears'
  return topName
}

// piped style
const sortByScoreDesc = sort((a, b) => b.score - a.score)
const getName = prop('name')
const getTopName = pipe(sortByScoreDesc, head, getName)

const result = getTopName(teams)
```
