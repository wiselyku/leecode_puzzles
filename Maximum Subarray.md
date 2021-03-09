###### tags: `Lecode Questions`
# 53. Maximum Subarray

https://leetcode.com/problems/maximum-subarray/

Basic Idea: Use Kadane’s Algorithm to solve this question. This algorithm is a famous DP algorithm. 
https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/

```python=

class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        max_so_far = nums[0]
        curr_max = nums[0]
        
        for i in range(1,len(nums)):
            curr_max = max(nums[i], curr_max + nums[i])
            max_so_far = max(max_so_far,curr_max)
            
        
        return max_so_far


```