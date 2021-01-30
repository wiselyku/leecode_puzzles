###### tags: `Lecode Questions`
# 8. String to Integer (atoi)

https://leetcode.com/problems/string-to-integer-atoi/

Basic ideas:
The idea is straightforward.  Just check all possible case 

My Solution:
```python=
class Solution:
    def myAtoi(self, s: str) -> int:

        # remove spaces until the first none space character
        index = 0
        for i in range(len(s)):
            if s[i] != " ":
                break
            
            if s[i] == " ":
                index = index + 1
                
            if s[i].isdigit() != True and s[i] != " ":
                break
                
        s = s[index:]
        print(s)
        
        #check the length of the s
        if len(s) == 0:
            return 0
        
        # if the length of s is 1
        if len(s) == 1:
            if s.isdigit() != True:
                return 0
        
        # check the first character, the first character can only be - or + or digit
        if s[0] != '-' and s[0] != '+' and s[0].isdigit() != True :
            return 0

        # check the second character, the second character should be digit
        if len(s) >= 2 and s[1].isdigit() != True and s[0].isdigit() != True:
            return 0
        # when we meet non-digital character get rid of the rest
        for i in range(1, len(s)):
            if s[i].isdigit() != True:
                s = s[0:i]
                break
        
        number = int(s)
        if number < -2147483648:
            return -2147483648
        elif number > 2147483647:
            return 2147483647
        else:
            return number
        



```