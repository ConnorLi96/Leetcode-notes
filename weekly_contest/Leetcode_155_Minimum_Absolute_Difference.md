
**Questions**
Given an array of distinct integers arr, find all pairs of elements with the minimum absolute difference of any two elements. 

Return a list of pairs in ascending order(with respect to pairs), each pair [a, b] follows

a, b are from arr
a < b
b - a equals to the minimum absolute difference of any two elements in arr

**Example**
```
Input: arr = [4,2,1,3]
Output: [[1,2],[2,3],[3,4]]
Explanation: The minimum absolute difference is 1. List all pairs with difference equal to 1 in ascending order.

Input: arr = [1,3,6,10,15]
Output: [[1,3]]

Input: arr = [3,8,-10,23,19,-4,-14,27]
Output: [[-14,-10],[19,23],[23,27]]
```

**KNOWLEDGE POINTS**
- get the min of absolute difference 


**Solution**

```
class Solution(object):
    def minimumAbsDifference(self, arr):
        arr.sort(reverse = True)
        def get_min(arr):
            min_arr = arr[0]
            for i in range(len(arr) -1):
                if arr[i] - arr[i+1] < min_arr:
                    min_arr = arr[i] - arr[i+1]

            return min_arr
        
        min_arr = get_min(arr)
        ans = []
        for item in arr[1:]:
            if arr[0] - item == min_arr:
                ans.append([item,arr[0]])

            arr.remove(arr[0])
        
        ans.sort()
        return ans
```

