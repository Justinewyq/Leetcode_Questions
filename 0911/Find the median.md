# Find the median

https://practice.geeksforgeeks.org/problems/find-the-median0527/1

```python
class Solution:
	def find_median(self, v):
		# Code here
		v.sort()
		if len(v) % 2 == 1:
		    return v[len(v) // 2]
		else:
		    a = v[len(v) // 2 - 1]
		    b = v[len(v) // 2]
		    return (a + b) // 2
```

* Time: O(n * logn)
* Space: O(1)
