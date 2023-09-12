# Spirally traversing a matrix

https://practice.geeksforgeeks.org/problems/spirally-traversing-a-matrix-1587115621/1

Didn't pass test in GFG, but the code works well in colab.

```python
class Solution:
    
    #Function to return a list of integers denoting spiral traversal of matrix.
    def spirallyTraverse(self,matrix, r, c): 
        # code here 
        level = 0
        result = []
        while level <= min(r, c) // 2:
            print(level)
            # left -> right
            for i in range(level, c - level - 1):
                result.append(matrix[level * c + i])
            # up -> bottom
            for i in range(level, r - level - 1):
                print(i)
                result.append(matrix[i * c + c - level - 1])
            # right -> left
            for i in range(c - level - 1, level, -1):
                result.append(matrix[(r - level - 1) * c + i])
            # bottom -> up
            for i in range(r - level - 1, level, -1):
                result.append(matrix[i * c + level])
            level += 1
            
        return result
```
