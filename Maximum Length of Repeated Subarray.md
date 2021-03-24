###### tags: `Lecode Questions`

# 718. Maximum Length of Repeated Subarray

https://leetcode.com/problems/maximum-length-of-repeated-subarray/

Basic Idea: Use the same idea of Longest common subsequence to solve this puzzle.  Just a modification can solve this puzzle.



```python=

class Solution:
    def findLength(self, A: List[int], B: List[int]) -> int:
        LCS = []
        answer = 0
        for i in range(len(A)):
            tmp = []
            for j in range(len(B)):
                tmp.append(0)
                
            LCS.append(tmp)
            
        for i in range(len(A)):
            for j in range(len(B)):
                if i == 0 or j == 0:
                    if A[i] == B[j]:
                        LCS[i][j] = 1
                
                else:
                    if A[i] == B[j]:
                        LCS[i][j] = 1 + LCS[i-1][j-1]
                        if LCS[i][j] > answer:
                            answer = LCS[i][j]
                        
        return answer

```

![](https://i.imgur.com/fSK6I13.png)
