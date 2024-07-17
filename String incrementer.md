# String incrementer [5 kyu]

#regex #strings

Your job is to write a function which increments a string, to create a new string.

- If the string already ends with a number, the number should be incremented by 1.
- If the string does not end with a number. the number 1 should be appended to the new string.

Examples:

`foo -> foo1`

`foobar23 -> foobar24`

`foo0042 -> foo0043`

`foo9 -> foo10`

`foo099 -> foo100`

_Attention: If the number has leading zeros the amount of digits should be considered._

---
## JavaScript

```javascript
function incrementString (strng) {
  let number = 0;
  let current = '';
  
  for (let i=strng.length-1; i>=0; i--) {
    if (!isNaN(parseInt(strng[i]))) {
      current = strng[i] + current
    }
    else {
      break
    }
  }
  
  let word = strng.slice(0,strng.length-current.length)
  let newNum = (parseInt(current)+1).toString()
  
  let result;
  
  if (current.length-newNum.length>=0){
    result =  word+'0'.repeat(current.length-newNum.length)+newNum;
  }
  else if (newNum!='NaN') {
    result = word+newNum
  }
  else {
    result = word + '1'
  }
  
  return result
}
```

---
## Python

```python
def increment_string(strng):
    current = ''
    
    for i in strng[::-1]:
        if i.isnumeric():
            current = i + current
        else:
            break
    
    if not current:
        return strng+'1'
    else:
        num = f"{(int(current)+1):0{len(current)}d}"
        return strng[:-len(current)]+num

```

---
## C++

```c++
#include <string>
#include <iostream>
using namespace std;

string incrementString(const string &str)
{ 
    
    string number = "";

    for (int i=str.length()-1; i>=0; i--) {
      char c = str[i];
      if ('0'<=c && c<='9') {
        number = c+number;
      }
      else {
        break;
      }
    }
    
    if (number.length()>0) {
      string newNum = to_string(stoi(number)+1);
      if (newNum.length()<number.length()) {
        for (int i=newNum.length(); i<int(number.length()); i++) {
          newNum = "0" + newNum;
        }
      }
      int newLen = str.length() - number.length();
      string result = "";
      
      for (int i=0; i<newLen; i++) {
        result += str[i];
      }
      
      return result+newNum;
    }
    else {
      return (str + "1");
    }
}
```

---