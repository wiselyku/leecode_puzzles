###### tags: `Lecode Questions`
# 236. Lowest Common Ancestor of a Binary Tree

https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/?fbclid=IwAR2mt-iWHL6u3Go8bBFEAZXM2Qg_KJtBRVe5nZghEXmQKOy3BUGcgJt0MdE

Basic idea: 
Solution 1: use BFS to traverse the tree and use the ancester information to find the LCA 
Solution 2: use DFS to traverse the tree.  If you found p or q, then mark every ancestor of p(or q) 1.  If you find a node has been marked twice then it would be the LCA.

My Solution:

```python=

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
# Solution 1

import queue
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        original_mapping = dict()
        nodes_mapping = dict()
        node_queue = queue.Queue()
        node_queue.put(root)
        original_mapping[root.val] = root
        # use BFS to visit all nodes in the binary tree
        while node_queue.empty() != True:
            node = node_queue.get()
            if node.left != None:
                node_queue.put(node.left)
                nodes_mapping[node.left.val] = node.val
                original_mapping[node.left.val] = node.left
            
            if node.right != None:
                node_queue.put(node.right)
                nodes_mapping[node.right.val] = node.val
                original_mapping[node.right.val] = node.right
        
        # collect all ancestor of node p 
        node_p = p.val
        p_ancestors = dict()
        p_ancestors[node_p] = 1
        while node_p in nodes_mapping.keys():
            p_ancestors[nodes_mapping[node_p]] = 1
            node_p = nodes_mapping[node_p]
        
        # check which q's lowest ancestor is also the ancestor of p's
        node_q = q.val
        found = 0
        while found != 1:
            if node_q in p_ancestors.keys():
                return original_mapping[node_q]
            
            node_q = nodes_mapping[node_q]
                    
        
       # print(p_ancestors)
       
```       
-----------------------------------------------------

```python=
# Solution 2 
#

class Solution:
	# Constructor to initialize result.
    def __init__(self):
        self.result = None
    
	# Helper Function
    def __helper(self, node, p, q):
        mid = 0 # If our "p" or "q" value falls on current node we will use mid value
        
        # Recursion Base Case.
        if not node:
            return 0
        
		# Recurse over left and right sub-trees.
        left = self.__helper(node.left, p, q)
        right = self.__helper(node.right, p, q)
		
		# Checking if our current node if one of the target node.
        if node == p or node == q:
            mid = 1
        
		# Checking if we satisfy any two values from all three ones.
        if mid + left + right == 2:
            self.result = node
        
		# We could find our target node at either position.
        return mid or left or right
        
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        self.__helper(root, p, q)
        return self.result
                
```
        
        




