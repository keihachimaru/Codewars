# Vowel Count [7 kyu]

#strings #fundamentals 

Return the number (count) of vowels in the given string.

We will consider `a`, `e`, `i`, `o`, `u` as vowels for t his Kata (but not `y`).

The input string will only consist of lower case letters and/or spaces.

---
## JavaScript

```javascript
function getCount(str) {
  return Array.from(str).filter(i => 'aeiou'.includes(i)).length;
}
```

---
## C++

```c++
#include <string>

using namespace std;

int getCount(const string& inputStr) {
  int num_vowels = 0;

  for (int i=0; i<int(inputStr.length()); i++) {
    char letter = inputStr[i];
    if (
      letter == 'a' ||
      letter == 'e' ||
      letter == 'i' ||
      letter == 'o' ||
      letter == 'u'
    ) {
      num_vowels += 1;
    }
  }
  
  return num_vowels;
}
```

---
## Python

```python
def get_count(sentence):
    return len([i for i in sentence if i in 'aeiou'])
```

---
