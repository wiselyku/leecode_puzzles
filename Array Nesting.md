###### tags: `Lecode Questions`

# 565. Array Nesting

https://leetcode.com/problems/array-nesting/

Basic Idea: The idea is just to calculate S[i].  After checking, you will find out that to find the longest S[i], you will not need to calculate each S[i].  Some S[i]s are in the same cycle.  Therefore, for each A[i], you only need to visit it once.



```python=

class Solution:
    def arrayNesting(self, nums: List[int]) -> int:
        max_nest = -1
        visit = []
        for i in range(len(nums)):
            visit.append(0) 
        
        
        for i in range(len(nums)):
            count = 1
            if visit[i] == 0:
                tmp = nums[i]
                visit[i] = 1
                while tmp != i:
                    tmp = nums[tmp]
                    visit[tmp] = 1
                    count = count + 1
                    
                if max_nest < count:
                    max_nest = count
        
        return max_nest
                    
```