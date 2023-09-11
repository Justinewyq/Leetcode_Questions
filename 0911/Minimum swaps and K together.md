# Minimum swaps and K together

https://practice.geeksforgeeks.org/problems/minimum-swaps-required-to-bring-all-elements-less-than-or-equal-to-k-together4847/1

## Solution

* Sliding window question. The size of the window is the no. of values <= k.
* Check the number of `swaps` among every window and find the minimum.

```python
class Solution:
        
    def minSwap (self,arr, n, k) : 
        #Complete the function
        # total no. of values <= k
        # also the size of the sliding window
        total = 0
        for i in range(n):
            if arr[i] <= k:
                total += 1
        swap = 0
        result = n
        i = 0
        while i < total:
            if arr[i] > k:
                swap += 1
            i += 1
        result = min(result, swap)
        while i < n:
            if arr[i - total] > k and arr[i] <= k:
                swap -= 1
            elif arr[i - total] <= k and arr[i] > k:
                swap += 1
            i += 1
            result = min(result, swap)
        return result
```

* Time: O(n)
* Space: O(1)
