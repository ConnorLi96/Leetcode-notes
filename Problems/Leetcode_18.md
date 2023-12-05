
## 1. [18. 4Sum](https://leetcode.com/problems/4sum/)

**Solution**
```
class Solution(object):
    def fourSum(self, nums, target):
        nums.sort() # ASC
        result = set()

        for i in range(len(nums) - 3):
            for j in range(i + 1, len(nums) - 2):
                left = j + 1
                right = len(nums) - 1 

                while left < right:
                    curr = nums[i] + nums[j] + nums[left] + nums[right]

                    if curr == target:
                        result.add((nums[i], nums[j], nums[left], nums[right]))
                        left += 1
                        right -= 1
                    elif curr < target:
                        left += 1 
                    else:
                        right -= 1

        return list(result)
```