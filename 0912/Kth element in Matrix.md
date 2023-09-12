# Kth element in Matrix

https://practice.geeksforgeeks.org/problems/kth-element-in-matrix/1

## Solution
* Similar to finding median in Matrix.
* Using binary search. `minv` and `maxv` as the searching boundary.


```python
def kthSmallest(mat, n, k): 
    # Your code goes here
    minv = mat[0][0]
    maxv = mat[0][n - 1]
    for i in range(n):
        minv = min(minv, mat[i][0])
        maxv = max(maxv, mat[i][n - 1])
    
    cur_pos = 0
    while minv < maxv:
        
        mid = (minv + maxv) // 2
        for i in range(n):
            for j in range(n):
                if mat[i][j] <= mid:
                    cur_pos += 1
                else:
                    break
        #print(mid, minv, maxv, cur_pos)
        if cur_pos < k:
            minv = mid + 1
        else:
            maxv = mid
        
        cur_pos = 0
    return minv
```

* Time: O(K * logN)
