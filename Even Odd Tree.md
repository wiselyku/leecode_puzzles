###### tags: `Lecode Questions`

# 1609. Even Odd Tree
https://leetcode.com/problems/even-odd-tree/

Basic Idea: The idea is to traverse each level of the tree and check if the values are satisfied the definition of the question.

```python=

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isEvenOddTree(self, root: TreeNode) -> bool:
        queue = []
        odd_or_even = 0
        if root.val%2 != 1:
            return False
        
        if root.left != None:
            queue.append(root.left)
            
        if root.right != None:
            queue.append(root.right)
        
        stop = root
        while len(queue)>0:
            stop = queue[-1]
            odd_or_even = odd_or_even + 1
            while stop != queue[0]:
                tmp = queue.pop(0)
                if tmp.left != None:
                    queue.append(tmp.left)
                    
                if tmp.right != None:
                    queue.append(tmp.right)
                    
                if odd_or_even%2 == 1:             
                    if tmp.val%2 != 0:
                        return False
                    
                    else:
                        if tmp.val <= queue[0].val:
                            return False
                        
                elif odd_or_even%2==0:

                    if tmp.val%2 != 1:
                        return False
                    
                    else:
                        if tmp.val >= queue[0].val:
                            return False
            
            if odd_or_even%2 == 1: 
                if stop.val%2 != 0:
                    return False
                
            else: 
                if stop.val%2 != 1:
                    return False
            
            if stop.left != None:
                queue.append(stop.left)
                
            if stop.right!= None:
                queue.append(stop.right)
                
            queue.pop(0)

        return True

```

![](https://i.imgur.com/jTuBauc.png)
