###### tags: `Lecode Questions`
# 287. Find the Duplicate Number

https://leetcode.com/problems/find-the-duplicate-number/?fbclid=IwAR3DX30MibNeuYN5lMpZyqLA6ZYDDquviXrlIBsGFOaor-F6w6ppKmtdkys

Basic Idea:
This question is easy.  You can try to sort the array and then check if there exist two continuous indice with the same integer.  Or you can build a hash table and then store each integer one by one.  If you find out an integer has been already stored in the hash table then this integer is the answer.


```python=

class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        hash_table = dict()
        for i in range(len(nums)):
            if nums[i] in hash_table:
                return nums[i]
            else:
                hash_table[nums[i]] = 1

```

