###### tags: `Lecode Questions`

# 371. Sum of Two Integers

https://leetcode.com/problems/sum-of-two-integers/

Basic Idea: The idea is to use bit operations. That is & , ^ and ~.  Where & -> and, ^ -> XOR, ~ -> not.


```python=

class Solution:
    def getSum(self, a: int, b: int) -> int:
        if a*b >=0:
            while (b != 0):
                carry = a & b
                a = a ^ b
                b = carry << 1
            
            return a
            
        else:
            if b > 0:
                tmp = b
                b = -a
                a = tmp
            else:
                b = -b
                
            if a >= b:    
                while (b != 0):
                    carry = ~a & b 
                    a = a ^ b
                    b = carry << 1
                    
                return a
            
            else: 
                while (a != 0):
                    carry = ~b & a 
                    b = b ^ a
                    a = carry << 1
                    
                return -b
                    

```