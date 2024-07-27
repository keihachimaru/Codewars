# Convert number to reversed array of digits [8 kyu]

#fundamentals #arrays

Given a random non-negative number, you have to return the digits of this number within an array in reverse order.

## Example(Input => Output):

```
35231 => [1,3,2,5,3]
0 => [0]
```

---
## C++

```c++
std::vector<int> digitize(unsigned long n) 
{ 
  if (n==0) {
    return {0};
  }
  std::vector<int> digits;
  while (n>0) {
    int digit = n%10;
    n = (n-digit)/10;
    digits.push_back(digit);
  }
  return digits;
}
```

---

