###### tags: `Lecode Questions`

# 556. Next Greater Element III

https://leetcode.com/problems/next-greater-element-iii/

Basic Idea: For each digit, we find the smallest number which is larger than the item in the back of the item.
For example, 489325721, for the first digit 4, the smallest number which is larger than it is the number 5.


```python=
class Solution:
    def nextGreaterElement(self, n: int) -> int:
        n_array = []
        tmp = n
        while tmp != 0:
            n_array.insert(0,tmp%10)
            tmp = int(tmp/10)
         
        stack = []
        res = [-1] * len(n_array)
        for i in range(len(n_array)-1):
            j = i+1
            target = 10
            while j<len(n_array):
                if n_array[i] < n_array[j] and n_array[j] < target:
                    target = n_array[j] 
                    res[i] = j
                    
                j = j + 1
        
        
        print(res)
        index = len(n_array) - 1  
        while index >=0:
            if res[index] != -1:
                swap = n_array[index]
                n_array[index] = n_array[res[index]]
                n_array[res[index]] = swap
                n_array[index+1:len(n_array)+1] = sorted(n_array[index+1:len(n_array)+1])
                break
            else:
                index = index -1
         
        
        if res[index] != -1:
            answer = "" 
            for item in n_array:
                answer = answer + str(item)
            
            
            if int(answer) < 2147483648:
                return answer
            
            else:
                return -1
            
        else:
            return -1
        
        


```
test cases:
1. 2147483486
2. 230241
3. 2147483476


