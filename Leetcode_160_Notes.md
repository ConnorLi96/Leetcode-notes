

## 1. [Find Positive Integer Solution for a Given Equation](https://leetcode.com/contest/weekly-contest-160/problems/find-positive-integer-solution-for-a-given-equation/)



**Solution**
```
accroding to the constrains, for loop all the x,y and check return value whether equal with z will get solution

def findSolution(self, customfunction, z):
    low, high = 1, 1000       
    res = []
    while low <= 1000 and high <= 1000 and high >= 1:
        if customfunction.f(low, high)  == z:
            res.append([low, high])
            low += 1
            high -= 1
        elif customfunction.f(low,high) < z:
            low += 1
        else:
            high -= 1
    return res

```



## 2. [Circular Permutation in Binary Representation](https://leetcode.com/contest/weekly-contest-160/problems/circular-permutation-in-binary-representation/)

**KNOWLEDGE POINTS**
- Gray Code
- Python位运算符
- python3 
**Solutions**

```
Step1: map every number from 0 to 2^n - 1 to its Gray code,
Step2: find the start element, and make the array circularly offset by index.

class Solution:
    def circularPermutation(self, n: int, start: int) -> List[int]:
        array = list(map(self.binaryToGray, range(0, 2 ** n)))
        index = array.index(start)

        return array[index: ] + array[: index]

    def binaryToGray(self, n: int) -> int:
        return n ^ (n >> 1)

```
