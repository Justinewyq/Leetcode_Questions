# Find a specific pair in Matrix

https://www.geeksforgeeks.org/find-a-specific-pair-in-matrix/

Given an n x n matrix `mat[n][n]` of integers, find the maximum value of `mat(c, d) – mat(a, b)` over all choices of indexes such that both `c > a` and `d > b`.

## Solution
Use `br_max[i][j]` to save the max bottom right value from position (i, j).

```python
def Solution(mat):
  br_max = [[-99 for j in range(len(mat[0]))] for i in range(len(mat))]

  result = -99
  for i in range(len(mat) - 2, -1, -1):
    for j in range(len(mat[0]) - 2, -1, -1):
      br_max[i][j] = max(mat[i + 1][j + 1], br_max[i + 1][j], br_max[i][j + 1])
      result = max(result, br_max[i][j] - mat[i][j])
  #print(br_max)
  print(result)

mat = [[1, 2, -1, -4, -20 ],
        [-8, -3, 4, 2, 1 ], 
        [3, 8, 6, 1, 3],
        [-4, -1, 1, 7, -6],
        [0, -4, 10, -5, 1]]
Solution(mat)
```

* Time: O(n^2)
* Space: O(n^2)
