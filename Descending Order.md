# Descending Order

#fundamentals 

Your task is to make a function that can take any non-negative integer as an argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.

### Examples:

Input: `42145` Output: `54421`

Input: `145263` Output: `654321`

Input: `123456789` Output: `987654321`

---
## JavaScript

```javascript
function descendingOrder(n){
  let digits = Array.from(n.toString())
  
  for (let i=1; i<digits.length; i++) {
    let j = i
    while ((digits[j]>digits[j-1]) && (j>0)) {
      let temp = digits[j]
      digits[j] = digits[j-1]
      digits[j-1] = temp
      j -= 1
    }
  }
  
  return parseInt(digits.join(''))
}
```

---
## Python

```python
def descending_order(num):
    digits = list(str(num))
    
    for i in range(1,len(digits)):
        j = i
        while (digits[j]>digits[j-1]) and (j > 0):
            temp = digits[j]
            digits[j] = digits[j-1]
            digits[j-1] = temp
            j -= 1
    
    return int(''.join(digits))
```

---
## C++

```c++
#include <cinttypes>
#include <cmath>

#include <iostream>

uint64_t descendingOrder(uint64_t a)
{
  int length = log10(a)+1;
  
  if (length > 0) {
    int digits[length];
    int x = 0;
    while (a > 0) {
        digits[x] = a % 10;
        a /= 10;
        x ++;
    }
    
    for (int i=0; i<length; i++) {
      int j = i;
      while (digits[j]>digits[j-1] && (j > 0)) {
        int temp = digits[j];
        digits[j] = digits[j-1];
        digits[j-1] = temp;
        j--;
      }
    }
    
    uint64_t result = 0;
    for (int digit : digits) {
        result = result * 10 + digit;
    }
    
    return result;
  }
  
  return a;
}
```

---

