# Rearrange characters

https://practice.geeksforgeeks.org/problems/rearrange-characters4649/1?utm_source=geeksforgeeks&utm_medium=article_practice_tab&utm_campaign=article_practice_tab

## Solution
* Keep a counter `alpha_counter` to save the occurrence times of the 26 letters.
* If the max occurence is `> len(str) // 2 + 1`, then it is impossible, return -1.
* Else, fill the even number position first with the max occurrence letters.


```python
from collections import Counter
class Solution:
    def findNextMax(self, cntr):
        maxv = 0
        maxk = 0
        for k in cntr:
            if cntr[k] > maxv:
                maxv = cntr[k]
                maxk = k
        return maxk, maxv
    
    def rearrangeString(self, str):
        #code here
        str = list(str)
        #print(str)
        alpha_counter = Counter(str)
        
        k, num = self.findNextMax(alpha_counter)
        if num > len(str) // 2 + 1:
            return -1
            
        for i in range(0, len(str), 2):
            if num >= 0:
                str[i] = k
                num -= 1
            else:
                alpha_counter[k] = 0
                k, num = self.findNextMax(alpha_counter)
        for i in range(1, len(str), 2):
            if num >= 0:
                str[i] = k
                num -= 1
            else:
                alpha_counter[k] = 0
                k, num = self.findNextMax(alpha_counter)
        str = "".join(str)
        print(str)
        return str

#str = "geeksforgeeks"
str = "bbbbb"
sol = Solution()
print(sol.rearrangeString(str))
```
