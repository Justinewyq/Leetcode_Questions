# Sort an array of 0s, 1s and 2s

https://github.com/Justinewyq/Leetcode_Questions/new/main/0905

Given an array of size N containing only 0s, 1s, and 2s; sort the array in ascending order.

* Expected Time Complexity: O(N)
* Expected Auxiliary Space: O(1)

```python
class Solution:
    def sort012(self,arr,n):
        # code here
        zptr = 0
        while arr[zptr] == 0:
            zptr += 1
        cur = zptr + 1
        
        # Move all 0s to the begining
        while cur < n:
            if arr[cur] == 0:
                arr[zptr], arr[cur] = arr[cur], arr[zptr]
                zptr += 1
            cur += 1
        
        oneptr = zptr
        while arr[oneptr] == 1:
            oneptr += 1
        cur = oneptr + 1
        
        # Move all 1s to the front
        while cur < n:
            if arr[cur] == 1:
                arr[oneptr], arr[cur] = arr[cur], arr[oneptr]
                oneptr += 1
            cur += 1
```
