# Count the smiley faces [6 kyu]

#regex #fundamentals 

Given an array (arr) as an argument complete the function `countSmileys` that should return the total number of smiling faces.

Rules for a smiling face:

- Each smiley face must contain a valid pair of eyes. Eyes can be marked as `:` or `;`
- A smiley face can have a nose but it does not have to. Valid characters for a nose are `-` or `~`
- Every smiling face must have a smiling mouth that should be marked with either `)` or `D`

No additional characters are allowed except for those mentioned.

**Valid smiley face examples:** `:) :D ;-D :~)`  
**Invalid smiley faces:** `;( :> :} :]`

## Example

```
countSmileys([':)', ';(', ';}', ':-D']);       // should return 2;
countSmileys([';D', ':-(', ':-)', ';~)']);     // should return 3;
countSmileys([';]', ':[', ';*', ':$', ';-D']); // should return 1;
```

## Note

In case of an empty array return 0. You will not be tested with invalid input (input will always be an array). Order of the face (eyes, nose, mouth) elements will always be the same.

---
## JavaScript

```javascript
//return the total number of smiling faces in the array
function countSmileys(arr) {
  let count = 0;
  arr.forEach((e)=>{
    let isFace = true;
    isFace = ':;'.includes(e[0]) && 'D)'.includes(e[e.length-1]) 
    if(e.length==3) {
      isFace = isFace && '-~'.includes(e[1]);
    }
    if (isFace && e.length<4) {
      count += 1;
    }
  })
  return count;
}
```

---
## Python

```python
def count_smileys(arr):
    count = 0
    for s in arr:
        if len(s)==2:
            count += s[0]in':;' and s[1]in'D)'
        if len(s)==3:
            count += s[0]in':;' and s[1]in'~-' and s[2]in'D)'
    return count
```

---
## C++

```c++
int countSmileys(std::vector<std::string> arr)
{
  int count = 0;
  for (const std::string face: arr) {
    bool isFace = true;
    if (face.length()==3) {
      isFace = isFace&&(face[0]==':'||face[0]==';');
      isFace = isFace&&(face[1]=='-'||face[1]=='~');
      isFace = isFace&&(face[2]==')'||face[2]=='D');
    }
    if (face.length()==2) {
      isFace = isFace&&(face[0]==':'||face[0]==';');
      isFace = isFace&&(face[1]==')'||face[1]=='D');
    }
    if (isFace) {
      count += 1;
    }
  }
  return count;
}
```

---
