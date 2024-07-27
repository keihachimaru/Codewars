# Square(n) Sum [8 kyu]

#arrays #lists #fundamentals

Complete the square sum function so that it squares each number passed into it and then sums the results together.

For example, for `[1, 2, 2]` it should return `9` because 12+22+22=912+22+22=9.

---
## C++

```c++
#include <vector>

int square_sum(const std::vector<int>& numbers)
{
    int total = 0;
    for (int i : numbers) {
      total += i*i;
    }
    return total;
}
```
---
