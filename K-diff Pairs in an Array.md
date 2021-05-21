###### tags: `Lecode Questions`

# K-diff Pairs in an Array


https://leetcode.com/problems/k-diff-pairs-in-an-array/

Basic Idea: We first sort the array and then use two indexes to check pairs.  If the difference between two values of the pair equals to k, accmulate the count.


```python=

class Solution:
    def findPairs(self, nums: List[int], k: int) -> int:
        sort_array = []
        sort_array = nums
        sort_array.sort()
        print(sort_array)
        index_i = 0 
        index_j = 1
        if len(nums) == 1:
            return 0
        
        count = 0
        while index_i != len(nums)-1:
            if sort_array[index_j] - sort_array[index_i] == k:
                if index_i != index_j:
                    count = count + 1
                    
                if index_j == len(nums)-1:
                    return count
                
                elif index_i == index_j:
                    index_j = index_j+1
                    
                else:
                    tmp = index_j+1
                    while sort_array[index_j] == sort_array[tmp]:
                        tmp = tmp + 1
                        if tmp == len(nums):
                            return count
                        
                    index_j = tmp
                
            elif sort_array[index_j] - sort_array[index_i] > k:
                index_i = index_i +1
                
            elif sort_array[index_j] - sort_array[index_i] < k:
                index_j = index_j +1
                if index_j == len(nums):
                    return count
            
        return count


```