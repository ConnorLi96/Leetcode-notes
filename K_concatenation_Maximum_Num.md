**Questions:**

Given an integer array arr and an integer k, modify the array by repeating it k times.

For example, if arr = [1, 2] and k = 3 then the modified array will be [1, 2, 1, 2, 1, 2].

Return the maximum sub-array sum in the modified array. Note that the length of the sub-array can be 0 and its sum in that case is 0.

As the answer can be very large, return the answer modulo 10^9 + 7.


**Examples:**
```
Input: arr = [1,2], k = 3
Output: 9


Input: arr = [1,-2,1], k = 5
Output: 2


Input: arr = [-1,-2], k = 7
Output: 0
```


**Solutions1 Wrong Answer:**

```
class Solution(object):
    def kConcatenationMaxSum(self, arr, k):
        def max_arr(arr):
            for item in arr:
                if item < 0:
                    arr.remove(item)
            return sum(arr)

        if sum(arr) ==0:
            return max_arr(arr)
        
        if max_arr(arr) > 0:
            if min(arr) < 0:
                return max_arr(arr) % (10*9+7)
            else:
                return (max_arr(arr) * k ) % (10*9+7)
        else:
            return 0
```

Reasons: The first func "max_arr" is wrong, if there are more than one negative number between positive number, you need get the single max one. This kind of problem can be summarized as ```max of sub_array``` 

