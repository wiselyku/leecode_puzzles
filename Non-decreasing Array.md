###### tags: `Lecode Questions`

# 665. Non-decreasing Array

https://leetcode.com/problems/non-decreasing-array/

Basic idea: 
Find the first one number which is larger than the next number and then try to change it to a reasonable number. Then, check the new sequence again to see if the new sequence is ok.


My Solution:
```python=
class Solution:
    def checkPossibility(self, nums: List[int]) -> bool:
        count = 0
        for i in range(len(nums)-1):
            # find the first one number that greater than the next number
            if nums[i] > nums[i+1]:
                # if there is still next next number, we should decide which one to change and change to what value
                if i < len(nums) -2:
                    if nums[i] > nums[i+2]:
                        nums[i] = nums[i+1]
                    else:
                        nums[i+1] = nums[i]                        
                else:
                    nums[i+1] = nums[i]
                break
        # after changing one number, re-check if the current sequence is ok                                    
        for i in range(len(nums)-1):
            if nums[i] > nums[i+1]:
                return False
            
        return True


```