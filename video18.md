#  Refactor a Promise Chain to Function Composition using Ramda
[Video](https://egghead.io/lessons/javascript-refactor-a-promise-chain-to-function-composition-using-ramda?pl=learn-ramda-js-ec318ad7)

```js
const deckUrl = 'https://deckofcardsapi.com/api/deck/new/shuffle/?cards=AS,2S,5C,3C,KD,AH,QH,2C,KS,8C'

// the promise chain
fetch(deckUrl)
  .then(res => res.json())
  .then(
    deck => fetch(`https://deckofcardsapi.com/api/deck${deck.deck_id}/draw/?count=10}`)
      .then(res => res.json())
  )
  .then(deck => deck.cards)
  .then(cards => cards.filter(c => c.suit === 'CLUBS'))
  .then(cards => cards.sort((c1, c2) => c1.value - c2.value))
  .then(cards => cards.map(c => c.image))
  .then(urls => urls.map(u => `<img width="100" src="${u}"/>`).join(''))
  .then(imgString => document.querySelector('#cards').innerHTML = `<div>${imgString}</div>`)

// ramda refactor
import { prop, filter, map, sortBy, propEq, join, compose, pluck } from 'ramda'

const getDeckId = prop('deck_id') // deck => deck.deck_id
const drawCards = id => fetch(`https://deckofcardsapi.com/api/deck${id}/draw/?count=10}`)
  .then(res => res.json())
const getCards = prop('cards') // deck => deck.cards
const justClubs = filter(propEq('suit' 'CLUBS')) // cards => cards.filter(c => c.suit === 'CLUBS')
const sortByValue = sortBy(prop('value')) // cards => cards.sort((c1, c2) => c1.value - c2.value)
const pluckImg = pluck('image') // cards => cards.map(c => c.image) or map(prop('image'))
const toImgString = compose(join(''), map(u => `<img width="100" src="${u}"/>`))
const render = imgString => document.querySelector('#cards').innerHTML = `<div>${imgString}</div>`

// compose all synchronous transforms together
const transformData = compose(toImgString, pluckImg, sortByValue, justClubs, getCards)

fetch(deckUrl)
  .then(res => res.json())
  .then(getDeckId)
  .then(drawCards)
  .then(transformData)
  //.then(getCards)
  //.then(justClubs)
  //.then(sortByValue)
  //.then(pluckImg)
  //.then(toImgString)
  .then(render)  
```
