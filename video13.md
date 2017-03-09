#  Count Words in a String with Ramda's countBy and invert
[Video](https://egghead.io/lessons/javascript-count-words-in-a-string-with-ramda-s-countby-and-invert?pl=learn-ramda-js-ec318ad7)

```js
import { match, countBy, identity, compose, toLower, invert, sortBy, map } from 'ramda'

const text = `
'have no fear of this mess,'
said the cat in the hat.
'i always pick up all my playthings
and so...
i will show you another
good trick that i know!'

then we saw him pick up all the things that were down.
he picked up the cake,
and the rake, and the gown,
and the milk, and the strings,
and the books, and the dish,
and the fan, and the cup,
and the ship, and the fish.
and he put them away.
then he said, 'that is that.'
and then he was gone
with a tip of his hat.

then our mother came in
and she said to us two,
'did you have any fun?
tell me.  what did you do?'

and sally and i did not know
what to say.
should we tell her
the things that went on there that day?

should we tell her about it?
now, what SHOULD we do?
well...
what would YOU do
if your mother asked YOU?`

const matchWords = match(/\w+/g) // strips spaces and punctuation
const results1 = matchWords(text) // -> ['have', 'no', 'fear', ...]

const countWords1 = compose(countBy(identity), matchWords)
const results2 = countWords1(text) // -> { SHOULD: 1, YOU: 2, a: 1, about: 1, ...}

const countWords2 = compose(countBy(toLower), matchWords)
const results3 = countWords2(text) // -> { have: 2, no: 1, fear: 1, ...}

const countWords3 = compose(invert, countBy(toLower), matchWords)
const results4 = countWords3(text) // -> { 1: ['no', 'fear', 'this', 'mess', ...], 2: [...], 3: [...], ...}

const countWords4 = compose(map(sortBy(identity)), invert, countBy(toLower), matchWords)
const results5 = countWords4(text) // -> { 1: ['a', 'about', 'always', 'another', ...], 2: [...], 3: [...], ...}
```
