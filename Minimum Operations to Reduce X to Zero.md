###### tags: `Lecode Questions`

# 1658. Minimum Operations to Reduce X to Zero

https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/

Basic Idea: The idea is to find the max subarray whose summation equals to summation of the whole array minus the x.  That is to find the max subarray whose summation equals to sum(nums) - x.


```python=

class Solution:
    def minOperations(self, nums: List[int], x: int) -> int:
        sum_of_array = 0 
        answer = 999999999
        for i in range(len(nums)):
            sum_of_array = sum_of_array + nums[i]
            
        # find the max subarray whose summation is equals to (sum_of_array -x)
        target = sum_of_array -x
        if target < 0:
            return -1
        
        elif target == 0:
            return len(nums)
        
        #print(target)
        prefix_index = 0
        current_sum = 0 
        for i in range(len(nums)):
            current_sum = current_sum + nums[i] 
            if current_sum == target:
                if answer > len(nums) - (i - prefix_index + 1):
                    answer = len(nums) - (i - prefix_index + 1)
                    current_sum = current_sum - nums[prefix_index]
                    prefix_index = prefix_index + 1
                 
            
            elif current_sum > target:
                while current_sum > target:
                    current_sum = current_sum - nums[prefix_index]
                    prefix_index = prefix_index + 1
                    
                if current_sum == target:
                    if answer > len(nums) - (i - prefix_index + 1):
                        answer = len(nums) - (i - prefix_index + 1)
                        current_sum = current_sum - nums[prefix_index]
                        prefix_index = prefix_index + 1
                
        
        if answer == 999999999:
            return -1
        else:
            return answer

```

test cases:
1. [5,2,3,1,1]  5
2. 


![](https://i.imgur.com/rXUgB7L.png)
