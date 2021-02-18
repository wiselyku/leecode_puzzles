###### tags: `Lecode Questions`
# 523. Continuous Subarray Sum

https://leetcode.com/problems/continuous-subarray-sum/


Basic Idea:
The idea is to check every subsequence in a more efficient way. My time complexity is O(n^2). This method is not very fast.  If you are interested in the question, you could try to figure out a better algorithm.  The boundary case should be careful.  


```python=

class Solution:
    def checkSubarraySum(self, nums: List[int], k: int) -> bool:
        sum = 0
        for i in range(len(nums)-1):
            sum = nums[i]
            for j in range(i+1,len(nums)):
                sum = sum +nums[j]
                if k!=0 and sum%k==0:
                    return True
                elif k==0 and sum==0:
                    return True
                
        return False

```

Test case:
1. 
[0,1,0]
0
2. 
[0,0]
0
3. 
[1,2,3]
0
