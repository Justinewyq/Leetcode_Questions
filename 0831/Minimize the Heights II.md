# Minimize the Heights II

https://practice.geeksforgeeks.org/problems/minimize-the-heights3351/1

Given an array `arr[]` denoting heights of `N` towers and a positive integer `K`.

For each tower, you must perform exactly one of the following operations exactly once.

* Increase the height of the tower by K
* Decrease the height of the tower by K
* 
Find out the minimum possible difference between the height of the shortest and tallest towers after you have modified each tower.


## Solution

Seperate the array into 2 part. The left part would increase by `K`, while the right part would decrease by `K`.

Iterate through the array, use `arr[i]` as the seperator.
* The max height at this step: `maxv = max(arr[i - 1] + k, arr[n - 1] - k)`
* The min height at this step: `minv = min(arr[i] - k, arr[0] + k)`

```python
class Solution:
    def getMinDiff(self, arr, n, k):
        # code here
        arr.sort()
        result = arr[n - 1] - arr[0]
        #print(arr)
        # numbers before arr[i] would increase by k
        # numbers after arr[i] (included) would decrease by k
        for i in range(1, n):
            if arr[i] < k:
                continue
            maxv = max(arr[i - 1] + k, arr[n - 1] - k)
            minv = min(arr[i] - k, arr[0] + k)
            #print(arr[i], maxv, minv)
            result = min(result, maxv - minv)
            
        return result
```

* Time: O(n * logn)
* Space: O(1)
