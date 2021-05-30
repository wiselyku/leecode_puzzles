###### tags: `Lecode Questions`

# 983. Minimum Cost For Tickets

https://leetcode.com/problems/minimum-cost-for-tickets/

Basic Idea: Use Dynamic Programming algorithm to count the minimum cost of each day in。the days array.



```python=

class Solution:
    def mincostTickets(self, days: List[int], costs: List[int]) -> int:
        DP = [0]*(len(days)+1)
        index07 = 0
        index30 = 0
        
        for i in range(len(days)):
            DP[i+1] = DP[i] + costs[0]
                                 
            while ( days[i] - days[index07] +1) > 7:
                index07 = index07 + 1
            
            tmp = DP[index07] + costs[1]
            if tmp < DP[i+1]:
                DP[i+1] = tmp
                
            while ( days[i] - days[index30] +1) > 30:
                index30 = index30 + 1  
                
            tmp = DP[index30] + costs[2]
            if tmp < DP[i+1]:
                DP[i+1] = tmp

                    
        
       # print(DP)
        return DP[len(days)]

```

test case:

[1,4,6,9,10,11,12,13,14,15,16,17,18,20,21,22,23,27,28]
[3,13,45]
