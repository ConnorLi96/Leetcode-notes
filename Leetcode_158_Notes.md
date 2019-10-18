### 1. [Split a String in Balanced Strings](https://leetcode.com/contest/weekly-contest-158/problems/split-a-string-in-balanced-strings/)

**Question**

Balanced strings are those who have equal quantity of 'L' and 'R' characters.

Given a balanced string s split it in the maximum amount of balanced strings.

Return the maximum amount of splitted balanced strings.

**Example**
```
Input: s = "RLRRLLRLRL"
Output: 4
Explanation: s can be split into "RL", "RRLL", "RL", "RL", each substring contains same number of 'L' and 'R'

Input: s = "RLLLLRRRLR"
Output: 3
Explanation: s can be split into "RL", "LLLRRR", "LR", each substring contains same number of 'L' and 'R'.
```

**Solutions**

Just set counts, if Rcount == Lcount then RESET Tcount as 0, finally return Tcount
```
Tcount = 0
Lcount = 0
Rcount = 0
def solution(s):
    for index, element in enumerate(s):
        if element == "R":
            Rcount +=1 
        else:
            Lcount += 1 

        if Lcount == Rcount:
            Tcount+=1 
            Rcount = 0
            Lcount = 0
    
    return Tcount
```

### 2. Queens that can attack Kings 
**[Questions & Examples](https://leetcode.com/contest/weekly-contest-158/problems/queens-that-can-attack-the-king/)**

**Solutions**
The Max number of valid Queens is 8 cause there are only 8 directions for king. So there are solutions as below:
- Start from the position of king,
- find out queens in 8 directions 
```
class Solution(object):
    def queensAttacktheKing(self, queens, king):
        res = []
        queens = {(i, j) for i,j in queens}
        for i in [-1, 0 ,1 ]:
            for j in [-1, 0 ,1]:
                for item in xrange(1, 8):
                    x, y = king[0] + item * i, king[1] + item * j
                    if (x, y) in queens:
                        res.append([x, y])
                        break # break means break up this branch judgement 
        return res
```
