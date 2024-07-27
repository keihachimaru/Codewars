# Find the odd int [6 kyu]

#fundamentals

Given an array of integers, find the one that appears an odd number of times.

There will always be only one integer that appears an odd number of times.

### Examples

`[7]` should return `7`, because it occurs 1 time (which is odd).  
`[0]` should return `0`, because it occurs 1 time (which is odd).  
`[1,1,2]` should return `2`, because it occurs 1 time (which is odd).  
`[0,1,0,1,0]` should return `0`, because it occurs 3 times (which is odd).  
`[1,2,2,3,3,3,4,3,3,3,2,2,1]` should return `4`, because it appears 1 time (which is odd).

---
## C++

```c++
#include <vector>
#include <iostream>

int findOdd(const std::vector<int>& numbers){
  std::vector <int> odd = { numbers[0] };
  for (size_t i=1; i<numbers.size(); i++) {
    bool add = true;
    size_t j = 0;
    while (add && j<odd.size()) {
      if (odd[j]==numbers[i]) {
        add = false;
        odd.erase(odd.begin() + j);
      }
      j ++;
    }
    if (add) {
      odd.push_back(numbers[i]);
    }
  }
  return odd[0];
}
```

---

