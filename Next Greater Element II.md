###### tags: `Lecode Questions`

# 503. Next Greater Element II

https://leetcode.com/problems/next-greater-element-ii/

Basic Idea: The idea is naive.  We just traverse the circular array for each item of the array.

Solution 1: 
```python=
class Solution:
    def nextGreaterElements(self, nums: List[int]) -> List[int]:
        answer = []
        for i in range(len(nums)):
            index = (i + 1)%len(nums)
            while index != i:
                if nums[i]< nums[index]:
                    answer.append(nums[index])
                    break
                else:
                    index = (index + 1) % len(nums)
                    
            
            if index == i:
                answer.append(-1)
        
        
        return answer
                
```

![](https://i.imgur.com/V0j4oVk.png)


Solution 2: This solution uses the stack to solve this question．If the next item is not larger than the top of the stack, put it into stack.  Else the next greater element will be the next item for the top of the stack.

```python=
class Solution:
    def nextGreaterElements(self, nums: List[int]) -> List[int]:
        res = [-1] * len(nums)
        stack = []
        for i in range(len(nums) * 2):
            while stack and nums[stack[-1]] < nums[i % len(nums)]:
                res[stack.pop()] = nums[i % len(nums)]
            stack.append(i % len(nums))
        return res

```

![](https://i.imgur.com/ffQWKAW.png)
