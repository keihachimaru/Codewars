# Most frequently used words in a text [4 kyu]

#strings #filtering #algorithms #regex 
## Assumptions: 

- A word is a string of letters (A to Z) optionally containing one or more apostrophes (`'`) in ASCII. 
- Apostrophes can appear at the start, middle or end of a word (`'abc`, `abc'`, `'abc'`, `ab'c` are all valid)
- Any other characters (e.g. `#`, `\`, `/` , `.` ...) are not part of a word and should be treated as whitespace.
- Matches should be case-insensitive, and the words in the result should be lowercased.
- Ties may be broken arbitrarily.
- If a text contains fewer than three unique words, then either the top-2 or top-1 words should be returned, or an empty array if a text contains no words.

## Examples:

```
"In a village of La Mancha, the name of which I have no desire to call to
mind, there lived not long since one of those gentlemen that keep a lance
in the lance-rack, an old buckler, a lean hack, and a greyhound for
coursing. An olla of rather more beef than mutton, a salad on most
nights, scraps on Saturdays, lentils on Fridays, and a pigeon or so extra
on Sundays, made away with three-quarters of his income."

--> ["a", "of", "on"]


"e e e e DDD ddd DdD: ddd ddd aa aA Aa, bb cc cC e e e"

--> ["e", "ddd", "aa"]


"  //wont won't won't"

--> ["won't", "wont"]
```

## Bonus points (not really, but just for fun):

1. Avoid creating an array whose memory footprint is roughly as big as the input text.
2. Avoid sorting the entire array of unique words.


---
## JavaScript

```javascript
function valid(char) {
  return (char >= 'a' && char <= 'z') || (char >= 'A' && char <= 'Z') || char === "'";
}

function topThreeWords(text) {
    text = text.toLowerCase().split('').map(c => valid(c) ? c : ' ').join('')
    let words = text.split(' ').filter(char => char!='')
    let wordsCount = {}
    for (let i=0; i<words.length; i++) {
      let word = words[i];
      if (word in wordsCount) {
        wordsCount[word] += 1
      }
      else if (!/^'+$/.test(word)) {
        wordsCount[word] = 1
      }
    }
    let items = Object.keys(wordsCount).map((key) => [key, wordsCount[key]])
    items.sort((a, b) => b[1] - a[1] || a[0].localeCompare(b[0]));
    return items.slice(0, 3).map((pair) => pair[0])
}
```

---