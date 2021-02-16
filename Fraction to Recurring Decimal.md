###### tags: `Lecode Questions`
# 166. Fraction to Recurring Decimal

https://leetcode.com/problems/fraction-to-recurring-decimal/

Basic Idea:
The idea is to observe the long division and find the pattern of repeating string. Since each fraction must be divided to a finite decimal, we do not need to worry it will be an infinit loop.


My Solution:
```python=

class Solution:
    def fractionToDecimal(self, numerator: int, denominator: int) -> str:
        # initial hash table
        hash_table = dict()
        index = 0
        start_index = 0
        answer = ""
        # handle the negative integer
        if numerator<0 and denominator>0:
            numerator = -numerator
            answer = answer+ "-"
        elif numerator>0 and denominator<0:
            denominator = -denominator
            answer = answer+ "-"
        elif numerator<0 and denominator<0:
            denominator = -denominator
            numerator = -numerator
        
        
        quotient = int(numerator/denominator)
        remainder = numerator%denominator
        # if remainder=0 return the answer
        if remainder == 0:
            return answer+str(quotient)
        
        answer = answer + str(quotient)+"."
        hash_table[remainder] = index
        index = index + 1
        #initial an array to store the numbers
        numbers = []
        # find the repeating string
        while remainder != 0:
            remainder = int(remainder)*10
            if remainder >= denominator:
                quotient = int(remainder/denominator)
                numbers.append(quotient)
                remainder = remainder%denominator
                if remainder in hash_table:
                    start_index = hash_table[remainder]
                    break
                else:
                    hash_table[remainder] = index
                    index = index + 1
            else:
                numbers.append(0)
                index = index + 1
                
        # concatenate the answer
        if remainder !=0:
            for i in range(start_index):
                answer = answer + str(numbers[i])
            
            answer = answer + "("
            for j in range(start_index, index):
                answer = answer + str(numbers[j])
                
            answer = answer + ")"
        else:
            for i in range(index-1):
                answer = answer + str(numbers[i])
        
        return answer

```
