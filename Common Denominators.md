# Common Denominators [5 kyu]

#fundamentals #algorithms #mathematics 

Common denominators

You will have a list of rationals in the form

```
{ {numer_1, denom_1} , ... {numer_n, denom_n} } 
or
[ [numer_1, denom_1] , ... [numer_n, denom_n] ] 
or
[ (numer_1, denom_1) , ... (numer_n, denom_n) ] 
```

where all numbers are positive ints. You have to produce a result in the form:

```
(N_1, D) ... (N_n, D) 
or
[ [N_1, D] ... [N_n, D] ] 
or
[ (N_1', D) , ... (N_n, D) ] 
or
{{N_1, D} ... {N_n, D}} 
or
"(N_1, D) ... (N_n, D)"
```

depending on the language (See Example tests) in which D is as small as possible and

```
N_1/D == numer_1/denom_1 ... N_n/D == numer_n,/denom_n.
```

#### Example:

```
convertFracs [(1, 2), (1, 3), (1, 4)] `shouldBe` [(6, 12), (4, 12), (3, 12)]
```

#### Note:

Due to the fact that the first translations were written long ago - more than 6 years - these first translations have only irreducible fractions.

Newer translations have some reducible fractions. To be on the safe side it is better to do a bit more work by simplifying fractions even if they don't have to be.

#### Note for Bash:

input is a string, e.g. `"2,4,2,6,2,8"` output is then `"6 12 4 12 3 12"`

---
## JavaScript

```javascript
function lcm(a, b) {
  return (a*b)/gcd(a, b);
}
function gcd(a, b) {
  if (b==0) {
    return a;
  }
  else {
    return gcd(b, a%b);
  }
}

function convertFrac(lst){
  if (lst.length) {
    let denominators = lst.map((pair) => pair[1]);
    let common = denominators.reduce((total, val)=>lcm(total, val));

    let fractions = lst.map((pair) => [(common/pair[1])*pair[0], common]);
    let result = fractions.map((pair)=>'('+pair.join(',')+')').join('');
    return result; 
  }
  return '';
}
```

---
## Python

```python
def gcd(a, b):
    if b==0:
        return a
    else:
        return gcd(b, a%b)
    
def lcm(a, b):
    return (a*b)/gcd(a, b)

def convert_fracts(lst):
    if len(lst)>0:
        denominators = list(map(lambda pair: pair[1], lst))
        common = denominators
        while len(common)!=1:
            common = [lcm(common[0], common[1])]+common[2:]
        common = int(common[0])
        fractions = [[(common//pair[1])*pair[0], common] for pair in lst]
        
        return fractions
    return []
    
```

---
## C++ 

```c++
#include <vector>
#include <string>
#include <numeric>  // for std::gcd

class Fracts
{
public:
    static unsigned long long gcd(unsigned long long a, unsigned long long b) {
        while (b != 0) {
            unsigned long long temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }

    static unsigned long long lcm(unsigned long long a, unsigned long long b) {
        return (a / gcd(a, b)) * b;
    }

    static std::string convertFrac(std::vector<std::vector<unsigned long long>>& lst) {
        if (lst.empty()) {
            return "";
        }

        unsigned long long common = lst[0][1];
        for (const auto& pair : lst) {
            common = lcm(common, pair[1]);
        }

        std::string result;
        for (const auto& pair : lst) {
            unsigned long long numerator = (common / pair[1]) * pair[0];
            result += "(" + std::to_string(numerator) + "," + std::to_string(common) + ")";
        }

        return result;
    }
};

```

---

