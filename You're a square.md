# You're a square [7 kyu]

#fundamentals #mathematics

### A square of squares

You like building blocks. You especially like building blocks that are squares. And what you even like more, is to arrange them into a square of square building blocks!

However, sometimes, you can't arrange them into a square. Instead, you end up with an ordinary rectangle! Those blasted things! If you just had a way to know, whether you're currently working in vain… Wait! That's it! You just have to check if your number of building blocks is a _perfect square_.

### Task

Given an integral number, determine if it's a [square number](https://en.wikipedia.org/wiki/Square_number):

> In mathematics, a **square number** or **perfect square** is an integer that is the square of an integer; in other words, it is the product of some integer with itself.

The tests will _always_ use some integral number, so don't worry about that in dynamic typed languages.

### Examples

```
-1  =>  false
 0  =>  true
 3  =>  false
 4  =>  true
25  =>  true
26  =>  false
```

---
## JavaScript

```javascript
var isSquare = function(n){
  return parseInt(n**0.5)**2 == n;
}
```

---
## Python

```python
def is_square(n):    
    return n>=0 and int(n**0.5)**2 == n
```

---
## C++

```c++
#include <cmath>
bool is_square(int n)
{
  int root = pow(n, .5);
  return pow(root, 2) == n;
}
```

---