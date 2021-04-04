###### tags: `Lecode Questions`

# 445. Add Two Numbers II

https://leetcode.com/problems/add-two-numbers-ii/

Basic Idea: The idea is sililar "Add Two Numbers".  Becareful the carry out and the direction of the link list.  

```python=

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        num1 = []
        num2 = []
        while l1 != None:
            num1.append(l1.val)
            l1 = l1.next
            
        while l2 != None:
            num2.append(l2.val)
            l2 = l2.next
        
        length = 0
        if len(num1) >= len(num2):
            length = len(num1)
        
        else:
            length = len(num2)
            
        index = 0 
        answer = [0]*length
        length1 = len(num1)
        for i in range(length1):
            answer[length-1-i] = answer[length-1-i] + num1[length1-1-i]
            

        length2 = len(num2)
        for i in range(length2):
            answer[length-1-i] = answer[length-1-i] + num2[length2-1-i] 
        
        
        carry = 0
        index = length - 1
        while index >= 0:
            answer[index] = answer[index] + carry
            if answer[index] >=10:
                answer[index] = answer[index] - 10
                carry = 1
            else:
                carry = 0
                
            index = index - 1
            
        if carry == 1:
            answer.insert(0,1)   
            
        l3 = ListNode(answer[0], None)
        l4 = l3

        for i in range(1, len(answer)):
            
            l5 = ListNode(answer[i], None)
            l4.next = l5
            l4 = l4.next
            
        return l3
        

```

![](https://i.imgur.com/uBBSlhw.png)
