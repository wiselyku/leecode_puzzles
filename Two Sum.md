###### tags: `Lecode Questions`
# 1. Two Sum

https://leetcode.com/problems/two-sum/

Basic Idea: Just use a hash table to solve this problem


```python=

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash_table = dict()
        answer = []
        for i in range(len(nums)):
            hash_table[nums[i]] = []
            
        
        for i in range(len(nums)):
            hash_table[nums[i]].append(i)
            
        
        print(hash_table)
        for i in range(len(nums)):
            tem = target - nums[i]
            if tem in hash_table:
                for j in range(len(hash_table[tem])):
                    if hash_table[tem][j] != i:
                        answer = [i,hash_table[tem][j]]
                        return answer
                        




```