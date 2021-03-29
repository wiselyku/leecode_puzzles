###### tags: `Lecode Questions`

# 238. Product of Array Except Self

https://leetcode.com/problems/product-of-array-except-self/

Basic Idea: The idea is straightforward.  


Solution 1
```python=

class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        zeros = 0 
        zero_index = -1
        answer = []
        product = 1
        for i in range(len(nums)):
            answer.append(0)
            if nums[i] == 0:
                zeros = zeros + 1
                zero_index = i
            
            else:
                product = product * nums[i]
                
                
                
        if zeros == 1:
            for i in range(len(nums)):
                if i == zero_index:
                    answer[i] = int(product)
                
                else:
                    answer[i] = 0
                    
        elif zeros == 0: 
            for i in range(len(nums)):
                answer[i] = int(product/nums[i])
                    
        return answer

```

Solution 2

```python=

class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        prefix_array = []
        suffix_array = []
        prefix_array.append(1)
        suffix_array.append(1)
        product = 1
        for i in range(len(nums)):
            product = product * nums[i]
            prefix_array.append(product)
            suffix_array.append(1)
            
        
        k = len(nums)
        product = 1
        for i in range(len(nums)):
            product = product * nums[k-i-1]
            suffix_array[k-i] = product
            
            
                   
        prefix_array.append(1)
        suffix_array.append(1)
        answer = []
        for i in range(len(nums)):
            tmp = prefix_array[i] * suffix_array[i+2]
            answer.append(int(tmp))
            

        return answer

```

![](https://i.imgur.com/ZWvauWV.png)
