
## 1. [18. 4Sum](https://leetcode.com/problems/4sum/)

**Solution1**
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

**Solution1**
```
class Solution(object):
    def fourSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        count = {}
        result = set()
        for item in nums:
            count[item] = count.get(item, 0) + 1

        for i in range(len(nums)):
            count[item] -= 1 
            for j in range(i+1, len(nums)):
                count[item] -= 1
                for k in range(j+1, len(nums)):
                    count[item] -= 1
                    complement = target - (nums[i] + nums[j] + nums[k])
                    if count.get(complement, 0) > 0:
                        result.add(tuple(sorted((nums[i], nums[j], nums[k], complement))))
                    count[item] += 1
                count[item] += 1
            count[item] += 1
        return result
```
        