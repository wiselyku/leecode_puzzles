###### tags: `Lecode Questions`

# 220. Contains Duplicate III

https://leetcode.com/problems/contains-duplicate-iii/

Basic idea:
We will need a balanced binary search tree for k nodes.  Every time we see a new value and input it to the tree and check which value is closest to it.  Then check if the absolute value is smaller than t.  Before we input the new value, we also remove the last k-th old value in the tree. So the total time complexity is O(nlogk).
https://runestone.academy/runestone/books/published/pythonds/Trees/SearchTreeImplementation.html

http://www.grantjenks.com/docs/sortedcontainers/introduction.html



My Solution:
```python=

import sortedcontainers
class Solution:
    def binarySearchNumbers(self, numbers: List[int], target: int) -> int:
        left = 0
        right = len(numbers)
        while right >= left:
            mid = int((right+left)/2)
            if numbers[mid] == target:
                return mid
            elif numbers[mid] > target:
                right = mid - 1
            else:
                left = mid + 1
                

    def containsNearbyAlmostDuplicate(self, nums: List[int], k: int, t: int) -> bool:
        sd = dict()
        sl = sortedcontainers.SortedList()
        if len(nums) == 0 or len(nums)==1:
            return False
        
        # deal with the case that k > len(nums)-1
        if k >= len(nums)-1:
            for i in range(len(nums)):
                if nums[i] in sl:
                    return True
                else:
                    sl.add(nums[i])
            
            print(sl)    
            for j in range(len(sl)-1):
                if abs(sl[j]-sl[j+1]) <= t:
                    return True
                
            return False
        
        
        # add first k numbers in to the dict and sortedlist
        for i in range(k+1):
            if nums[i] in sd:
                return True
            else:
                sd[nums[i]] = i
                
            sl.add(nums[i])
        
        #print(sl)
        # check if first k number fit the question definitions
        for i in range(k):
            if abs(sl[i]-sl[i+1]) <= t:
                return True
        
        
        # check the remaining numbers
        for i in range(k+1,len(nums)):
            sl.remove(nums[i-k-1])
            sl.add(nums[i])
            del sd[nums[i-k-1]]
            if nums[i] in sd:
                return True
            else:
                sd[nums[i]] = i
                
            # find the position of nums[i] in sl and then compare it with its neighbors.
            position = self.binarySearchNumbers(sl, nums[i])
            #check neighbors
            if position > 0:
                if abs(sl[position]-sl[position-1]) <= t:
                    return True
                
            if position < k:
                if abs(sl[position]-sl[position+1]) <= t:
                    return True
            
            
        return False
            

```