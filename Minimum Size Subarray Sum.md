###### tags: `Lecode Questions`

# 209. Minimum Size Subarray Sum

https://leetcode.com/problems/minimum-size-subarray-sum/

Basic Idea: The idea is to use the same idea of the Kadane’s Algorithm to find the minumum size subarray sum

```python=

class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        current_sum = 0 
        answer = 2147483647
        index = 0 
        for i in range(len(nums)):
            current_sum = current_sum + nums[i]
            if current_sum >= target:
                tmp = i - index + 1
                if answer > tmp:
                    answer = tmp
                
            while current_sum >= target:
                current_sum = current_sum - nums[index]
                index = index + 1
                if current_sum >= target:
                    tmp = i - index + 1
                    if answer > tmp:
                        answer = tmp
                        
        if answer == 2147483647:
            return 0
        else:
            return answer

```

test cases:
1. 11  [1,2,3,4,5]


![](https://i.imgur.com/1k4hgmV.png)

