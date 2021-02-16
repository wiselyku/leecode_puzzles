###### tags: `Lecode Questions`
# 151. Reverse Words in a String

https://leetcode.com/problems/reverse-words-in-a-string/

Basic Idea:
The idea is straightforward.  Just split the string into words and output them backwards.

```python=
class Solution:
    def reverseWords(self, s: str) -> str:
        words = s.split()
        answer =""
        for i in range(len(words)):
            if i != len(words)-1:
                answer = answer+ words[len(words)-i-1] + " "
            else:
                answer = answer+words[len(words)-i-1]
                
        return answer

```