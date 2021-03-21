###### tags: `Lecode Questions`

# 1590. Make Sum Divisible by P

https://leetcode.com/problems/make-sum-divisible-by-p/

Basic Idea: The idea is to use a prefix sum array and a hash table to find the subarray.


```python=

class Solution:
    def minSubarray(self, nums: List[int], p: int) -> int:
        prefix_sum = []
        prefix = 0
        hash_table = dict()
        answer = 100000
        for i in range(len(nums)):
            prefix = prefix + nums[i]
            prefix_sum.append(prefix)
            ramainder = prefix % p 
            if ramainder in hash_table:
                hash_table[ramainder].append(i)
                
            else:
                hash_table[ramainder] = [i]
                   

                            
        remainder = prefix % p
        if remainder == 0:
            answer = 0
            return answer
        
        else: 
            for i in range(len(prefix_sum)):
                if prefix_sum[i] % p == remainder and answer > i:
                    answer = i + 1
                    
                tmp = (prefix_sum[i] - remainder) % p
                if tmp in hash_table:
                    for j in range(len(hash_table[tmp])):
                        if hash_table[tmp][j] < i:
                            if answer > i-hash_table[tmp][j]:
                                answer = i - hash_table[tmp][j]
                            
                        else:
                            break
          
        
        
        if answer == len(nums):
            return -1
            
        else:
            return answer

```