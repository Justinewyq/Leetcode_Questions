# Smallest Distinct Window

https://practice.geeksforgeeks.org/problems/smallest-distant-window3132/1

```python
class Solution:
    def findSubString(self, str):
        # Your code goes here
        counter = {}
        for x in str:
            if x not in counter:
                counter[x] = 0
        
        distinct_chars = len(counter)
        
        left = 0
        cur = 0
        result = len(str)
        
        for i in range(len(str)):
            counter[str[i]] += 1
            if counter[str[i]] == 1:
                cur += 1
            if cur == distinct_chars:
                while counter[str[left]] > 1:
                    counter[str[left]] -= 1
                    left += 1
                result = min(result, i - left + 1)
        
        return result
```
