# Binary Addition [7 kyu]

#binary #fundamentals 

Implement a function that adds two numbers together and returns their sum in binary. The conversion can be done before, or after the addition.

The binary number returned should be a string.

**Examples:(Input1, Input2 --> Output (explanation)))**

```
1, 1 --> "10" (1 + 1 = 2 in decimal or 10 in binary)
5, 9 --> "1110" (5 + 9 = 14 in decimal or 1110 in binary)
```

---
### JavaScript

```javascript
function addBinary(a,b) {
  return (a+b).toString(2);
}
```

---
### Python

```python
def add_binary(a,b):
    return bin(a+b)[2:];
```

---
### C++

```c++
#include <cstdint>
#include <string>
#include <cmath>

using namespace std;

string add_binary(uint64_t a, uint64_t b) {
    uint64_t c = a+b;
    string result;

    if (c==0) {
      return "0";
    }

    while (c>0) {
      result = (c % 2 == 0 ? "0" : "1") + result;
      c /= 2;
    }

    return result;
}
```
