**Questions**
Given an array of integers arr, write a function that returns true if and only if the number of occurrences of each value in the array is unique.

**Examples**
```
Input: arr = [1,2,2,1,1,3]
Output: true

Input: arr = [1,2]
Output: false

Input: arr = [-3,0,1,-3,1,1,1,-3,10,0]
Output: true

```
**KNOWLEDGE POINTS**
- the occurrences of each elements in list 
- set, no repeat elements list

**Solution1**
Just get the counter of each element in list, and then compare the length of ```set of result``` and the result, could know is there unique value in array.
```
def solution2(arr):
    ans_list = list(dict(Counter(arr)).values())
    if len(Counter(ans_list)) == len(ans_list):
        return True
    else:
        return False
```

**Solution2**
```
def solution_666(arr):
    ct = Counter(arr)
    return len(set(ct.values())) == len(ct.values())
```

**The Best Counter Algorthim**
```


https://blog.csdn.net/sunshine__0411/article/details/80792970
```
