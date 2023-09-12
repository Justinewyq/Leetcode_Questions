# Median in a row-wise sorted Matrix

https://practice.geeksforgeeks.org/problems/median-in-a-row-wise-sorted-matrix1527/1

```python
from bisect import bisect_right
class Solution:
    def median(self, matrix, R, C):
    	#code here 
    	left = matrix[0][0]
    	right = matrix[0][C - 1]
    	for i in range(R):
    	    left = min(left, matrix[i][0])
    	    right = max(right, matrix[i][C - 1])
    	
    	mid_pos = (R * C + 1) // 2
    	
    	while left < right:
    	    mid = (left + right) // 2
    	    smaller = 0
    	    for i in range(R):
    	        # the values <= mid
    	        smaller += bisect_right(matrix[i], mid)
    	    
    	    if smaller < mid_pos:
    	        left = mid + 1
    	    else:
    	        right = mid
        return left
```
