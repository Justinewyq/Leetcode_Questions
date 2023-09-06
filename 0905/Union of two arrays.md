# Union of two arrays

https://practice.geeksforgeeks.org/problems/union-of-two-arrays3538/1

```python
class Solution:    
    #Function to return the count of number of elements in union of two arrays.
    def doUnion(self,a,n,b,m):
        s = set()
        for x in a:
            if x not in s:
                s.add(x)
        for x in b:
            if x not in s:
                s.add(x)
        return len(s)
```
* Time: O(n + m)
* Space: O(n + m)
