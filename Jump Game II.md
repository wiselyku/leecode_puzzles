###### tags: `Lecode Questions`

# 45. Jump Game II


https://leetcode.com/problems/jump-game-ii/

Basic Idea: Design a greedy algorithm to solve this puzzle.  



```python=

class Solution:
    def jump(self, nums: List[int]) -> int:
        index = 0
        current_max = 0 
        target_index = 0
        jump = nums[0]
        count = 0
        if len(nums) == 1:
            return 0
        
        while index != len(nums)-1:
            if index + nums[index] >= len(nums)-1:
                return count+1
            
            current_max = 0 
            for i in range(1,jump+1):
                if current_max < index + i +nums[index+i]:
                    current_max = index + i +nums[index+i]
                    target_index = index + i
            
                             
            jump = nums[target_index]
            index = target_index
            count = count + 1


```

![](https://i.imgur.com/B8dtqIK.png)
