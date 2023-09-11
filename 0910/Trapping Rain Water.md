# Trapping Rain Water

https://practice.geeksforgeeks.org/problems/trapping-rain-water-1587115621/1

* 2 lists `lmax` and `rmax` to store the max left and right height we can support at place i.
```python
class Solution:
    def trappingWater(self, arr,n):
        #Code here
        lmax = [0] * n
        rmax = [0] * n
        cur_max = arr[0]
        for i in range(n):
            lmax[i] = cur_max
            cur_max = max(cur_max, arr[i])
        cur_max = arr[n - 1]
        for i in range(n - 1, -1, -1):
            rmax[i] = cur_max
            cur_max = max(cur_max, arr[i])
            
        result = 0
        for i in range(1, n - 1):
            height = min(lmax[i], rmax[i])
            if height > arr[i]:
                result += height - arr[i]
        return result
```
