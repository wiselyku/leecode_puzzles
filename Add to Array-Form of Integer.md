###### tags: `Lecode Questions`

# 989. Add to Array-Form of Integer

https://leetcode.com/problems/add-to-array-form-of-integer/

Basic Idea: The idea is naive but you may need to be careful about some cases.  

```python=
class Solution:
    def addToArrayForm(self, A: List[int], K: int) -> List[int]:
        length = len(A)
        lengthK = len(str(K))
        index = 0
        if lengthK > length:
            for i in range(lengthK-length):
                A.insert(0,0)
            length = lengthK
            
            
        while lengthK > 0:
            tmp = K % 10
            A[length-1-index] = A[length-1-index] + tmp
            index = index + 1
            lengthK = lengthK -1
            K = int(K/10)
            
        carry = 0
        index = length - 1
        while index >= 0:
            A[index] = A[index] + carry
            if A[index] >=10:
                A[index] = A[index] - 10
                carry = 1
            else:
                carry = 0
                
            index = index - 1
            
        if carry == 1:
            A.insert(0,1)
            
        return A
        
            


```

test case:
1. [0]  23


![](https://i.imgur.com/DH9nr90.png)
