Given a boolean 2D array of n x m dimensions where each row is sorted. Find the 0-based index of the first row that has the maximum number of 1's.

* Iterate by column, once a 1 is found, return the row number.
```python
class Solution:

	def rowWithMax1s(self,arr, n, m):
		# code here
		for i in range(m):
		    for j in range(n):
		        if arr[j][i] == 1:
		            return j
		return -1

```
