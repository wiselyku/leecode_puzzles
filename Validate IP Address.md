###### tags: `Lecode Questions`
# 468. Validate IP Address

https://leetcode.com/problems/validate-ip-address/

Basic Idea: The idea is naive.  But, there are many boundary cases. You should be more careful about the boundary cases.


```python=

class Solution:
    def validIPAddress(self, IP: str) -> str:
        Count_dot = IP.count(".")
        if Count_dot != 3 and Count_dot != 0:
            return "Neither"
        
        IP = IP.replace("."," ")
        Count_semicolon = IP.count(":")
        if Count_semicolon != 0 and Count_semicolon !=7:
            return "Neither"
        
        IP = IP.replace(":"," ")
        IP_array = IP.split()
        IPv6 = ['0','1','2','3','4','5','6','7','8','9','a','A','b','B','c','C','d','D','e','E','f','F'] 
        if len(IP_array) == 4:
            for i in range(4):
                if IP_array[i]<"0" or IP_array[i]>"255":
                    return "Neither"
                elif len(IP_array[i])>=2 and IP_array[i][0]=="0":
                    return "Neither"
                elif len(IP_array[i])>3:
                    return "Neither"
                
            return "IPv4"
        elif len(IP_array) == 8:
            for i in range(8):
                if len(IP_array[i])>4:
                    return "Neither"
                
                for j in range(len(IP_array[i])):
                    if IP_array[i][j] not in IPv6:
                        return "Neither"
                
            return "IPv6"
        else:
            return "Neither"
        


```

Test Case:
1. "01.01.01.01"
2. "2001:0db8:85a3:00000:0:8A2E:0370:7334"
3. "11111.1111.111.111111"

