
**Questions:**
A bus has n stops numbered from 0 to n - 1 that form a circle. We know the distance between all pairs of neighboring stops where distance[i] is the distance between the stops number i and (i + 1) % n.

The bus goes along both directions i.e. clockwise and counterclockwise.

Return the shortest distance between the given start and destination stops.


**Examples:**:

```
Input: distance = [1,2,3,4], start = 0, destination = 1
Output: 1
Explanation: Distance between 0 and 1 is 1 or 9, minimum is 1.
```


```
Input: distance = [1,2,3,4], start = 0, destination = 2
Output: 3
Explanation: Distance between 0 and 2 is 3 or 7, minimum is 3.
```


```
Input: distance = [1,2,3,4], start = 0, destination = 3
Output: 4
Explanation: Distance between 0 and 3 is 6 or 4, minimum is 4.
```

**Solutions: AC**:

In this case, get the shortest distance is our goal, and we just need to consider two conditions, start > des, des < start. And in this two conditions, we also need consider the clockwise and counterclockwise. So the steps as below:

- get distance with clockwise and counterclockwise
- compare result and return the short one
- add if and else to hold the condition des < start.

```
```


**Optimise solutions:**
Altough the last has been accpetd, the solution can be optimised in enumerate(), cause the sum() will make the process complexity to O(m*n), so we can optimise it like thinking slicing window. The steps as below:

```
```

