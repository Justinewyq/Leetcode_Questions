# Chocolate Distribution Problem

https://practice.geeksforgeeks.org/problems/chocolate-distribution-problem3825/1

```python
class Solution:

    def findMinDiff(self, A,N,M):

        # code here
        A.sort()
        i = 0
        result = A[N - 1] - A[0]
        while i + M - 1 < N:
            result = min(result, A[i + M - 1] - A[i])
            i += 1
        return result
```

* Time: O(n * logn)
* Space: O(1)
