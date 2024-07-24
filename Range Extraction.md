# Range Extraction [4 kyu]

#algorithms

A format for expressing an ordered list of integers is to use a comma separated list of either

- individual integers
- or a range of integers denoted by the starting integer separated from the end integer in the range by a dash, '-'. The range includes all integers in the interval including both endpoints. It is not considered a range unless it spans at least 3 numbers. For example "12,13,15-17"

Complete the solution so that it takes a list of integers in increasing order and returns a correctly formatted string in the range format.

**Example:**

```javascript
solution([-10, -9, -8, -6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20]);
// returns "-10--8,-6,-3-1,3-5,7-11,14,15,17-20"
```

_Courtesy of rosettacode.org_

---
## JavaScript

```javascript
function solution(list){
  let before;
  let ranges = [list[0].toString()];
  let range = 0;
  
  //Iterate through the elements in the list
  for (let i=1; i<list.length; i++) {
    before = list[i-1];
    let current = list[i];
    
    //Check if the numbers are next to each other
    if (Math.abs(current-before)==1) {
      //If they are track the distance
      range += 1;
    }
    else {
      //Don't add the dash unless the interval is greater than one
      if (range>1) {
        ranges[ranges.length-1] += '-'+before.toString();
      }
      else if (range==1) {
        ranges.push(before.toString());
      }
      //Reset interval range
      range = 0
      ranges.push(current.toString());
    }
  }
  
  //For the last number in the list
  
  //If it ends in an interval (last number is end of interval)
  //Repeat the else part of the for loop
  if (range>1) {
    ranges[ranges.length-1] += '-'+list[list.length-1];
  }
  else if (range==1) {
    ranges.push(list[list.length-1])
  }
  
  //Convert to formated string
  return ranges.join(',');
}

```
---