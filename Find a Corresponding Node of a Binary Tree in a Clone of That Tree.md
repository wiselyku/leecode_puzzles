###### tags: `Lecode Questions`

# 1379. Find a Corresponding Node of a Binary Tree in a Clone of That Tree

https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/

Basic Idea: I use BFS to check which node in original is the same to target.  Then, i find the cloned node in the cloned tree.



```python=

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def getTargetCopy(self, original: TreeNode, cloned: TreeNode, target: TreeNode) -> TreeNode:
        queue = []
        count = 0
        queue.append(original)
        while len(queue)>0:
            node = queue.pop(0)
            count = count + 1
            if node == target:
                break
                
            if node.left!= None:
                queue.append(node.left)
                
            if node.right!= None:
                queue.append(node.right)
        
        queue = []
        queue.append(cloned)
        while len(queue)>0:
            node = queue.pop(0)
            count = count - 1
            if count == 0 :
                return node
            
            if node.left!= None:
                queue.append(node.left)
                
            if node.right!= None:
                queue.append(node.right)            



```