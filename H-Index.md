###### tags: `Lecode Questions`

# 274. H-Index

https://leetcode.com/problems/h-index/

Basic Idea: The idea is to sort the array first and then count the value h.

```python=

class Solution:
    def hIndex(self, citations: List[int]) -> int:
        citations.sort(reverse=True)
        h = 0
        for i in range(len(citations)):
            if citations[i] >= i+1:
                h = h + 1
                
        return h

```