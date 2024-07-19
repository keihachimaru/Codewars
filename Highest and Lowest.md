# Highest and Lowest [7 kyu]

#fundamentals #strings

In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

### Examples

```python
high_and_low("1 2 3 4 5")  # return "5 1"
high_and_low("1 2 -3 4 5") # return "5 -3"
high_and_low("1 9 3 4 -5") # return "9 -5"
```

### Notes

- All numbers are valid `Int32`, no _need_ to validate them.
- There will always be at least one number in the input string.
- Output string must be two numbers separated by a single space, and highest number is first.

---
## JavaScript

```javascript
function highAndLow(numbers){
  let nums = numbers.split(' ').map((a) => parseInt(a));
  return Math.max(...nums) + ' ' + Math.min(...nums);
}
```

---
## Python

```python
def high_and_low(numbers):
    nums = [int(i) for i in numbers.split(' ') if i!=' ']
    return str(max(nums)) + ' ' + str(min(nums))
```

---
## C++

```c++
#include <string>
using namespace std;

string highAndLow(const string& numbers){
  vector<int> nums;
  string temp = "";
  string strng = numbers + " ";
  for (int i=0; i<int(strng.size()); i++) {
    if (strng[i]==' ') {
      nums.push_back(stoi(temp));
      temp = "";
    }
    else {
      temp += strng[i];
    }
  }
  int min = nums[0];
  int max = nums[0];
  for (const int n : nums) {
    if (n > max) {
      max = n;
    }
    if (n < min) {
      min = n;
    }
  }
  return to_string(max) + " " + to_string(min);
}
```

---
