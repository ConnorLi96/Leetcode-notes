### [Check If It Is a Straight Line](https://leetcode.com/contest/weekly-contest-159/problems/check-if-it-is-a-straight-line/)

You are given an array coordinates, coordinates[i] = [x, y], where [x, y] represents the coordinate of a point. Check if these points make a straight line in the XY plane.

**Examples**

```
Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
Output: true
```


```
Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
Output: false
```

**KNOWLEDGE POINT**
- Slope, if the point in one straight line, then the slope of each point to the point1 and point2 should be same.
- then the slope k == (y3 - y1)/(x3 - x1) == (y3 - y2)/(x3 - x2)
- in order to avoid the 0, (y3 - y2) * (x3 -x1) == (x3 -x2) * (y3 - y1)

**Solution**

```
(x1, y1) , (x2,y2) =  coordinates[:2]
for x3,y3 in coordinates:
  if (y3 - y2) * (x3 -x1) =! (x3 -x2) * (y3 - y1):
    return False
return True
```

### Replace the Substring for Balanced String



