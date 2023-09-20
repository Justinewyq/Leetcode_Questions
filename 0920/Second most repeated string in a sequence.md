# Second most repeated string in a sequence

https://practice.geeksforgeeks.org/problems/second-most-repeated-string-in-a-sequence0534/1

* Build a map to save all strings and its occurences.
* Find the 2nd most frenquent string by iterate the map.

  
```python
class Solution:
    def secFrequent(self, arr, n):
        # code here
        dic = {}
        maxv = 0
        secv = 0
        maxk = ""
        seck = ""
        for s in arr:
            if s in dic:
                dic[s] += 1
            else:
                dic[s] = 1
        
        for k, v in dic.items():  
            if v > maxv:
                secv = maxv
                seck = maxk
                maxv = v
                maxk = k
            elif v > secv:
                secv = v
                seck = k
        return seck
```

* Time: O(n)
* Space: O(n)
