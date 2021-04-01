###### tags: `Lecode Questions`
# 2. Add Two Numbers

https://leetcode.com/problems/add-two-numbers/

Basic Idea: The idea is naive. Just calculate it in a link list way.


```python=
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        answer = []
        carry = 0
        while l1 != None and l2 != None:
            tmp = l1.val + l2.val + carry
            if tmp > 9:
                tmp = tmp % 10
                carry = 1
                answer.append(tmp)
            else:
                answer.append(tmp)
                carry = 0
                
            l1 = l1.next
            l2 = l2.next
            
        if l1 != None:
            while l1 != None:
                tmp = l1.val + carry
                if tmp > 9:
                    tmp = tmp % 10
                    carry = 1
                    answer.append(tmp)
                else:
                    answer.append(tmp)
                    carry = 0
                
                l1 = l1.next
                
                
        if l2 != None:
            while l2 != None:
                tmp = l2.val + carry
                if tmp > 9:
                    tmp = tmp % 10
                    carry = 1
                    answer.append(tmp)
                else:
                    answer.append(tmp)
                    carry = 0    
                    
                l2 = l2.next
                
        if carry == 1:
            answer.append(1)
            
            
        l3 = ListNode(answer[0], None)
        l4 = l3

        for i in range(1, len(answer)):
            
            l5 = ListNode(answer[i], None)
            l4.next = l5
            l4 = l4.next
            
            
        return l3
        
```

![](https://i.imgur.com/B5ez0Oc.png)
