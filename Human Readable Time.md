# Human Readable Time [5 kyu]

#date_time #mathematics #algorithms

Write a function, which takes a non-negative integer (seconds) as input and returns the time in a human-readable format (`HH:MM:SS`)

- `HH` = hours, padded to 2 digits, range: 00 - 99
- `MM` = minutes, padded to 2 digits, range: 00 - 59
- `SS` = seconds, padded to 2 digits, range: 00 - 59

The maximum time never exceeds 359999 (`99:59:59`)

You can find some examples in the test fixtures.

---
## JavaScript

```javascript
function humanReadable (seconds) {
  let hours = parseInt(seconds/3600);
  hours = hours<10 ? '0'+hours : hours.toString();
  
  seconds = seconds%3600;
  let minutes = parseInt(seconds/60);
  minutes = minutes<10 ? '0'+minutes : minutes.toString();
  
  seconds = seconds%60;
  seconds = seconds<10 ? '0'+seconds : seconds.toString();
  
  return hours+':'+minutes+':'+seconds
}
```

---