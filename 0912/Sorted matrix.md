# Sorted matrix

https://practice.geeksforgeeks.org/problems/sorted-matrix2333/1

2D Matrix -> 1D array -> sort -> 2D Matrix

```python
class Solution:
    def sortedMatrix(self,N,Mat):
        #code here
        mat_list = []
        for i in range(N):
            for j in range(N):
                mat_list.append(Mat[i][j])
        mat_list.sort()
        for i in range(N):
            for j in range(N):
                Mat[i][j] = mat_list[i * N + j]
        return Mat
```

* Time: O(N^2 * logN)
* Space: O(N ^ 2)
