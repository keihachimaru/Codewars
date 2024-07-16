# Number of People in the Bus [7 kyu]

#fundamentals

There is a bus moving in the city which takes and drops some people at each bus stop.

You are provided with a list (or array) of integer pairs. Elements of each pair represent the number of people that get on the bus (the first item) and the number of people that get off the bus (the second item) at a bus stop.

Your task is to return the number of people who are still on the bus after the last bus stop (after the last array). Even though it is the last bus stop, the bus might not be empty and some people might still be inside the bus, they are probably sleeping there :D

Take a look on the test cases.

Please keep in mind that the test cases ensure that the number of people in the bus is always >= 0. So the returned integer can't be negative.

The second value in the first pair in the array is 0, since the bus is empty in the first bus stop.

---
## JavaScript

```javascript
var number = function(busStops){
  return busStops.map((e) =>  e[0]-e[1] ).reduce((total, val) => val + total)
}
```

---
## Python

```python
def number(bus_stops):
    return sum([a[0]-a[1] for a in bus_stops])
```

---
## C++

```c++
#include <utility>
#include <vector>

unsigned int number(const std::vector<std::pair<int, int>>& busStops){
  int total = 0;
  for (const std::pair stop: busStops) {
    total += stop.first - stop.second;
  }
  return total;
}
```

---
