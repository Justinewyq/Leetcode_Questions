# Count Inversions

https://practice.geeksforgeeks.org/problems/inversion-of-array-1587115620/1

Inversion Count: For an array, inversion count indicates how far (or close) the array is from being sorted. If the array is already sorted then the inversion count is 0.

If an array is sorted in the reverse order then the inversion count is the maximum.

* Time: O(N * logN)
* Space: O(N)

## Solution
1. Use heapq to store the pair of (val, index) in ascending order.
2. Pop each pair, and use `bisect` to find how many smaller value on its left.


```python
from heapq import heappush, heappop
from bisect import bisect, insort

class Solution:
    #User function Template for python3
    
    # arr[]: Input Array
    # N : Size of the Array arr[]
    #Function to count inversions in the array.
    def inversionCount(self, arr, n):
        # Your Code Here
        sortpair = []
        for i in range(len(arr)):
            heappush(sortpair, (arr[i], i))
        
        # visited = [1] * len(arr)
        x = []
        result = 0
        while sortpair: # O(n)
            v, ind = heappop(sortpair)
            #inv = sum(visited[ : ind]) # O(n)
            #visited[ind] = 0
            #print(v, inv)
            y = bisect(x, ind) # O(logN)
            inv = ind - y
            result += inv
            insort(x, ind)
        return result
```
