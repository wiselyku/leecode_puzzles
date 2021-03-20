###### tags: `Lecode Questions`

# 974. Subarray Sums Divisible by K

https://leetcode.com/problems/subarray-sums-divisible-by-k/

Basic Idea: The basic Idea is to use prefix sum and a hash table to solve this puzzle.  



```python=

class Solution:
    def subarraysDivByK(self, A: List[int], K: int) -> int:
        prefix_array = []
        prefix_sum = 0
        hash_table = dict()
        for i in range(len(A)):
            prefix_sum = prefix_sum + A[i]
            prefix_sum = prefix_sum % K
            prefix_array.append(prefix_sum)
            if prefix_sum in hash_table:
                hash_table[prefix_sum].append(i)
                
            else:
                hash_table[prefix_sum] = [i]
                
            
       # print(prefix_array)
       # print(hash_table)
        count = 0 
        for i in range(len(prefix_array)):
            if i == 0 and prefix_array[i] == 0:
                count = count + 1
            
            elif i > 0:
                if prefix_array[i] == 0:
                    count = count + 1
                
                tmp =  prefix_array[i]
                count = count + hash_table[tmp].index(i)

                   
        return count





```

test case:
There is a test which has a lot of 0s in the array. If your algorithm is not fast enough, your code will exceed the time limit.

![](https://i.imgur.com/1Ir23lM.png)

