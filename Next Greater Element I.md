###### tags: `Lecode Questions`

# 496. Next Greater Element I

https://leetcode.com/problems/next-greater-element-i/

Basic Idea: The algorithm is naive.  Find the value of nums1[i] in the nums2 list and then find the next greater element in the back of the number in the num2 list.  


```python=

class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        hash_table = dict()
        answer = []
        for i in range(len(nums2)):
            hash_table[nums2[i]] = i
            
        
        for i in range(len(nums1)):
            index = hash_table[nums1[i]]
            founded = -1
            while index < len(nums2):
                if nums2[index] > nums1[i]:
                    founded = 1
                    answer.append(nums2[index])
                    break
                else:
                    index = index + 1
                    
            if founded == -1:
                answer.append(-1)
                
        
        return answer
                
```
![](https://i.imgur.com/kZqvS30.png)
