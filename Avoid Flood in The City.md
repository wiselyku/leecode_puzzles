###### tags: `Lecode Questions`
# 1488. Avoid Flood in The City

https://leetcode.com/problems/avoid-flood-in-the-city/

Basic Idea:
I think the idea is a bit straightfoward. Sometimes, you just do not think that can be a good way to solve the question.  But, it works.  The idea is to remember each numbers last postion.  When you meet the same number check if there existed a remainder 0 which has not been used to dry the lake.  

```python=
class Solution:
    def avoidFlood(self, rains: List[int]) -> List[int]:
        stack = []
        answer = []
        lake_full = dict()
        zero_array = []
        for i in range(len(rains)):
            zero_array.append(1)
            
        stack.append(-1)
        for i in range(len(rains)):
            if rains[i]>0:
                if rains[i] in lake_full:
                    # find a zero to dry the lake
                    found = 0 
                    for j in range(len(stack)):
                        if lake_full[rains[i]] < stack[j] and stack[j]<i:
                            zero_array[stack[j]] = rains[i]
                            lake_full[rains[i]] = i
                            stack.pop(j)
                            found = 1
                            break
                    if found ==0:
                        return []

                else:
                    lake_full[rains[i]] = i
                    
            else:
                stack.append(i)
         
        
        for i in range(len(rains)):
            if rains[i]>0:
                answer.append(-1)
            else:
                answer.append(zero_array[i])
            
        print(answer)
        return answer
        
        
                    
```

test case:
1. [2,3,0,0,3,1,0,1,0,2,2]
2. [0,0,0,0,0,0,0,0,0,0,0,0,0,56438,0,0,76913,0,0,53492,0,50824,0,0,0,0,0,0,0,0,79212,0,0,0,0,0,0,36713,62045,79212,36713,56438,0,0,0,62045,0,76913,50824,0,0,0,0,0,53492,0]
