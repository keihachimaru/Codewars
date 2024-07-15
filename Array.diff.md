# Replace With Alphabet Position [6 kyu]

#arrays #fundamentals #algorithms

Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.

It should remove all values from list `a`, which are present in list `b` keeping their order.

`array_diff([1,2],[1]) == [2]`

If a value is present in `b`, all of its occurrences must be removed from the other:

`array_diff([1,2,2,2,3],[2]) == [1,3]`

---
## JavaScript

``` javascript
function arrayDiff(a, b) {
  return a.filter(i => !b.includes(i))
}
```

---
## Python

```python
def array_diff(a, b):
    return [i for i in a if not i in b]
```

---
