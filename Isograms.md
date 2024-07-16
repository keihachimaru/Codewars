# Isograms [7 kyu]

#strings #fundamentals 

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore the letter case.

## Example: (Input --> Output)

```
"Dermatoglyphics" --> true
"aba" --> false
"moOse" --> false (ignore letter case)
```

---
## Javascript

```javascript
function isIsogram(str){
  return str.length == new Set(Array.from(str.toLowerCase())).size
}
```

---
## Python

```python
def is_isogram(string):
    return len(string) == len(set(string.lower()))
```

---
## C++

```c++
#include <iostream>
using namespace std;

bool is_isogram(std::string str) {
  int length = str.length();
  int chars[length];
  int count = 0;
  bool it_is = true;
  
  while (it_is && count<length) {
    int letter = int(str[count]);
    if (65<=letter && letter<=90) {
      letter += 32;
    }
    
    for (int j=0; j<length; j++) {
      if (chars[j]==letter) {
        it_is = false;
      }  
    }
    
    chars[count] = letter;
    count ++;
  }
  
  return it_is;
}
```

---