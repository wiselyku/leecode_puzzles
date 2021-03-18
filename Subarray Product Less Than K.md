###### tags: `Lecode Questions`
# 713. Subarray Product Less Than K

https://leetcode.com/problems/subarray-product-less-than-k/

Basic Idea: The idea is to use a Dynamic Programming to solve this puzzle.  We calculate an opt function. opt(j) = i, where nums[i]* nums[i+1]*...* nums[j] < k.  Then we use the opt function to count the final answer. 


```python=

class Solution:
    def numSubarrayProductLessThanK(self, nums: List[int], k: int) -> int:
        index_i = 0
        opt = []
        product = 1
        for i in range(len(nums)):
            opt.append(-1)
        
        # calculate the opt function
        for i in range(len(nums)):
            product = product * nums[i]
            if product < k:
                opt[i] = index_i
            
            else:
                while index_i < i and product >= k:
                    product = product/nums[index_i]
                    index_i = index_i+1
                    if product < k and index_i <= i:
                        opt[i] = index_i
        
        
        #count the answer
        answer = 0
        for i in range(len(opt)):
            if i == 0 and opt[i] >-1:
                answer = answer + 1
                
            elif i > 0:
                if opt[i] > -1:
                    tmp = i - opt[i] + 1
                    answer = answer + tmp*(tmp+1)/2
                    if opt[i] <= i-1 and opt[i-1]>-1:
                        tmp = (i-1) - opt[i] + 1
                        answer = answer - tmp*(tmp+1)/2
            
                                
        return int(answer)
        

```

![](https://i.imgur.com/4XNTNXe.png)
