  
# Reversed Strings

#strings #fundamentals 

Complete the solution so that it reverses the string passed into it.

```
'world'  =>  'dlrow'
'word'   =>  'drow'
```

---
## C++

```c++
#include <string>
using namespace std ; 

string reverseString (string str )
{
  string result = "";
  for (const char c: str) {
    result = c + result;
  }
  return result;
}
```

---
