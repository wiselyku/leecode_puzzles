###### tags: `Lecode Questions`

# 55. Jump Game

https://leetcode.com/problems/jump-game/

Basic Idea: I just modify my solution of the puzzle "45. Jump Game II".  Then, it solves this puzzle successfully.

```python=

class Solution:
    def canJump(self, nums: List[int]) -> bool:
        index = 0
        current_max = 0 
        target_index = 0
        jump = nums[0]
        count = 0
        if len(nums) == 1:
            return True
        
        while index != len(nums)-1:
            if index + nums[index] >= len(nums)-1:
                return True
            
            current_max = 0 
            for i in range(1,jump+1):
                if current_max < index + i +nums[index+i]:
                    current_max = index + i +nums[index+i]
                    target_index = index + i
            
                             
            jump = nums[target_index]
            index = target_index
            count = count + 1
            if jump == 0:
                return False
            
        return False
  

```

![](https://i.imgur.com/JhyUpy4.png)
