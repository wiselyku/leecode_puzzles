###### tags: `Lecode Questions`

# 67. Add Binary

https://leetcode.com/problems/add-binary/

Basic Idea: The idea is to use binary addition in Python. And then transform the binary integer to a string. 

```python=

class Solution:
    def addBinary(self, a: str, b: str) -> str:
        integer_sum = int(a, 2) + int(b, 2)
        binary_sum = bin(integer_sum)
        answer = str(binary_sum)[2:]
        return answer

```

![](https://i.imgur.com/mwCpCha.png)
