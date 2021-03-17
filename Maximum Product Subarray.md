###### tags: `Lecode Questions`
# 152. Maximum Product Subarray

https://leetcode.com/problems/maximum-product-subarray/

Basic Idea: The idea is to use Dynamic Programming.  But, it may not be easy to figure out the dynamic programming algorithm.  At each step, we should know the current maxmum and current minmum when we see each entry of the array.  Since every two negative integer can form a positive integer after a multiplication, we need to keep the current minmum

```python=

class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        max_so_far=-2147483648
        curr_max=1
        curr_min=1
        for i in range(len(nums)):
            if nums[i]==0:
                curr_max=1
                curr_min=1
                
            tmp_max=curr_max
            tmp_min=curr_min
            curr_max=max(tmp_max*nums[i],tmp_min*nums[i],nums[i])
            curr_min=min(tmp_max*nums[i],tmp_min*nums[i],nums[i])
            if max_so_far<curr_max:
                max_so_far=curr_max
            
        return max_so_far                  
        

```
![](https://i.imgur.com/KNNf0MU.png)

test case:
1. [2,3,-2,4,-3,6,2,5,-3,10,6]
2. [-2]
3. [-1,-2,-9,-6]
4. [-2,-2,-9,-6,-3,-2]