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

**KNOWLEDGE POINTS**

- get the maximum of subarray 
```
def max_sub(arr):
    ans = cur = 0
    for i in arr:
        cur += n
    cur = max(cur, 0)
    m = max(cur, m)
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


**Solution2 TLE**

```
class Solution(object):
    def kConcatenationMaxSum(self, arr, k):
        def maxsub(arr):
            m = cur = 0
            for n in arr:
                cur += n # cur is the current sum 
                cur = max(cur, 0) # in case the 0 condition
                m = max(m, cur) # m once added next element, contrast the current sum and max_sum
            return m  


        mod = 10**9 + 7
        m1 = maxsub(arr)
        m2 = maxsub(arr+arr)

        if k == 1:
            return m1 % mod 
        elif k == 2:
            return m2 % mod 
        else:
            return maxsub(arr * k) % mod 
```
Reasons: ```return maxsub(arr * k) % mod ``` means O(n) complexitity, but if the k is very large, this range of array would be very long. So we can get the sum of single array, Multiply it with k, and plus the m1 or m2, like the solution below.

**Solution3**
```
class Solution(object):
    def kConcatenationMaxSum(self, arr, k):
        def maxsub(arr):
            m = cur = 0
            for n in arr:
                cur += n # cur is the current sum 
                cur = max(cur, 0) # in case the 0 condition
                m = max(m, cur) 
            return m  


        mod = 10**9 + 7
        m1 = maxsub(arr)
        m2 = maxsub(arr+arr)
        sum_single = sum(arr)
        
        if k == 1:
            return m1 % mod 
        elif k == 2:
            return m2 % mod 
        elif sum_single >0:
            return max((m1 + (k-1)*sum_single),(m2 + (k-2)*sum_single)) % mod
        else:
            return max(m1,m2)

```

