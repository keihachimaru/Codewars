# Replace With Alphabet Position [6 kyu]

#strings #fundamentals 

Welcome.

In this kata you are required to, given a string, replace every letter with its position in the alphabet.

If anything in the text isn't a letter, ignore it and don't return it.

`"a" = 1, "b" = 2, etc.`

## Example

```
Input = "The sunset sets at twelve o' clock."
Output = "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"
```

---
## JavaScript

``` javascript
function alphabetPosition(text) {
  let alphabet = 'abcdefghijklmnopqrstuvwxyz'
  let output = [];
  
  Array.from(text).forEach((e)=>{
    let letter = e.toLowerCase()
    if (alphabet.indexOf(letter)>-1) {
      output.push(alphabet.indexOf(letter)+1)
    }
  })

  return output.join(' ');
}
```


---
## C++

```c++
#include <string>
using namespace std;
string alphabet_position(const string &text) {
  string output = "";
  
  for (int i=0; i<text.length(); i++) {
    if ('A'<=text[i] && text[i]<='Z') {
      int num = int(text[i]) - 64;
      output += to_string(num) + " ";
    }
    else if ('a'<=text[i] && text[i]<='z') {
      int num = int(text[i]) - 96;
      output += to_string(num) + " ";
    }
  }
  
  if (output != "") {
    output.pop_back();
  }
  
  return output;
}
```

---
