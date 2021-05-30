###### tags: `Lecode Questions`

# 322. Coin Change


https://leetcode.com/problems/coin-change/

Basic Idea:



```python=
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        DP = []
        for i in range(amount+1):
            DP.append(0)
            
        for i in range(1,amount+1):
            for j in range(len(coins)):
                if i - coins[j] > 0:                   
                    if DP[i - coins[j]]>0:
                        tmp = DP[i - coins[j]] + 1
                        if DP[i] != 0:
                            DP[i] = min(tmp,DP[i])
                    
                        else:
                            DP[i] = DP[i - coins[j]]+1

                        
                elif i - coins[j] == 0:
                    DP[i] = 1
                        
        
        #print(DP)
        if amount == 0: 
            return 0
        
        elif DP[amount] == 0:
            return -1
        
        else:
            return DP[amount] 
        
```

test cases:

[186,419,83,408]
6249

[3,7,15,23]
123

