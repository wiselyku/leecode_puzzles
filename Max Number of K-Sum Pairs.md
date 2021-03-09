###### tags: `Lecode Questions`
# 1679. Max Number of K-Sum Pairs

https://leetcode.com/problems/max-number-of-k-sum-pairs/description/

Basic Idea:
This question is very similar to the two sum question. Just do a modification and then you can solve this question


```python=

class Solution:
    def maxOperations(self, nums: List[int], k: int) -> int:
        answer_pair = 0
        answer_diff = 0
        hash_table = dict()
        for i in range(len(nums)):
            if nums[i] in hash_table:
                hash_table[nums[i]] += 1
            else:
                hash_table[nums[i]] = 1
                
        
        for key in hash_table:
            count = hash_table[key]
            tem = k - key
            if tem in hash_table:
                if tem == key:
                    answer_pair = answer_pair + math.floor(hash_table[key]/2) 
                else:
                    if count <= hash_table[tem]:
                        answer_diff = answer_diff + count
                    else: 
                        answer_diff = answer_diff + hash_table[tem]
        
        answer = answer_pair + math.floor(answer_diff/2)
        return answer
                        

```
