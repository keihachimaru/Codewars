# Sum of two lowest positive integers [7 kyu]

#arrays #fundamentals 

Create a function that returns the sum of the two lowest positive numbers given an array of minimum 4 positive integers. No floats or non-positive integers will be passed.

For example, when an array is passed like `[19, 5, 42, 2, 77]`, the output should be `7`.

`[10, 343445353, 3453445, 3453545353453]` should return `3453455`.

---
## C++

```c++
#include <vector>
#include <climits>

long sumTwoSmallestNumbers(const std::vector<int>& numbers) {
    int first = INT_MAX;
    int second = INT_MAX;

    for (int number : numbers) {
        if (number < first) {
            second = first;
            first = number;
        } 
        else if (number < second) {
            second = number;
        }
    }
  
    return static_cast<long>(first) + second;
}

```

---
