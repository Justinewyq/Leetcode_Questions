# Minimum number of jump

https://practice.geeksforgeeks.org/problems/minimum-number-of-jumps-1587115620/1

```python
class Solution:
	def minJumps(self, arr, n):
	    #code here
	    jump = 1
	    bound = arr[0]
	    cur = arr[0]
	    p = 0
	    
	    for i in range(1, len(arr)):
	        # print(jump, i, arr[i], cur, bound)
	        if bound >= n - 1:
	            return jump
	        if i <= bound:
	            cur = max(cur, i + arr[i])
	        elif cur > bound:
	            bound = cur
	            cur = i + arr[i]
	            jump += 1
	        else:
	            return -1
	    return -1
```
