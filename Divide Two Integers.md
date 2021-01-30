###### tags: `Lecode Questions`

# 29. Divide Two Integers

https://leetcode.com/problems/divide-two-integers/

Basic idea:
The idea is straightforward.  Just reutrn the answer they want

My Solution:
```python=
import math
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        answer = dividend/divisor
        if answer > 0:
            answer = math.floor(answer)
            if answer > 2147483647:
                return 2147483647
            else:
                return answer
        else:
            answer = math.ceil(answer)
            if answer < -2147483648:
                return -2147483648
            else:
                return answer

```