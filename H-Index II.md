###### tags: `Lecode Questions`

# 275. H-Index II

https://leetcode.com/problems/h-index-ii/

Basic Idea: The idea is to use binry search to find the the value h.


```python=

class Solution:
    def hIndex(self, citations: List[int]) -> int:
        left = 0 
        right = len(citations) - 1
        answer = 0
        while left <= right:
            mid = int( (left+right)/2 )
            tmp = len(citations) - mid
            if citations[mid] >= tmp:
                answer = tmp
                right = mid - 1
                
            else:
                left = mid + 1
                
        
        return answer
                

```

![](https://i.imgur.com/6h4vO7k.png)
