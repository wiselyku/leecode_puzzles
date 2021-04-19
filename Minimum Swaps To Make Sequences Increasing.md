###### tags: `Lecode Questions`

# 801. Minimum Swaps To Make Sequences Increasing

https://leetcode.com/problems/minimum-swaps-to-make-sequences-increasing/

Basic Idea: Use Dynamic Programming, but the idea is not easy to think and to prove.


```python=

class Solution:
    def minSwap(self, A: List[int], B: List[int]) -> int:
        DPtable = []
        for i in range(len(A)):
            DPtable.append([2000,2000])
           
            
        DPtable[0][0] = 0
        DPtable[0][1] = 1
        
        for i in range(1, len(A)):
            tmpA = 0
            tmpB = 0
            if A[i] > A[i-1] and B[i] > B[i-1]:
                tmpA = DPtable[i-1][0]
            
            else:
                tmpA = 2000
                
            if A[i] > B[i-1] and B[i] > A[i-1]:
                tmpB = DPtable[i-1][1]
                
            else:
                tmpB = 2000
                
            DPtable[i][0] = min(tmpA, tmpB)
            
            if B[i] > A[i-1] and A[i] > B[i-1]:
                tmpA = DPtable[i-1][0]
            
            else:
                tmpA = 2000
                
            if B[i] > B[i-1] and A[i] > A[i-1]:
                tmpB = DPtable[i-1][1]
                
            else:
                tmpB = 2000
            
            DPtable[i][1] = min(tmpA, tmpB) + 1
            
            
        return min(DPtable[-1][0],DPtable[-1][1])
            
            
        


```

test cases
1. [0,4,4,5,9]  [0,1,6,8,10]

