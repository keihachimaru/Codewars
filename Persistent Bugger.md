# Persistent Bugger [6 kyu]

#fundamentals #mathematics 

Write a function, `persistence`, that takes in a positive parameter `num` and returns its multiplicative persistence, which is the number of times you must multiply the digits in `num` until you reach a single digit.

For example **(Input --> Output)**:

```
39 --> 3 (because 3*9 = 27, 2*7 = 14, 1*4 = 4 and 4 has only one digit, there are 3 multiplications)
999 --> 4 (because 9*9*9 = 729, 7*2*9 = 126, 1*2*6 = 12, and finally 1*2 = 2, there are 4 multiplications)
4 --> 0 (because 4 is already a one-digit number, there is no multiplication)
```

---
## JavaScript

```javascript
function persistence(num) {
   let n = 0;
  while (num.toString().length>1) {
    num = Array.from(num.toString()).reduce((total, val) => total*parseInt(val));
    n += 1;
  }
  return n;
}
```

---
## Python

```python
import numpy as np

def persistence(n):
    num = 0
    while len(str(n))>1:
        n = np.prod([int(i) for i in str(n)])
        num += 1
    return num
```

---
## C++

```c++

long long prod(long long n) {
  long long result = 1;
  while (n>0) {
    result *= n%10; 
    n /= 10;
  }
  return result;
}

int persistence(long long n){
  int num = 0;
  while (n>9) {
    n = prod(n);
    num += 1;
  }
  return num;
}
```

---