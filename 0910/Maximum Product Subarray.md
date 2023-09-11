# Maximum Product Subarray

https://practice.geeksforgeeks.org/problems/maximum-product-subarray3604/1

## Solution
* Use `minprod` and `maxprod` to store the min and max product value ending at `arr[i]`.
```python
class Solution:

	# Function to find maximum
	# product subarray
	def maxProduct(self,arr, n):
		# code here
		if n == 1:
		    return arr[0]
		
		# the min and max product ending at arr[i]
		minprod = arr[0]
		maxprod = arr[0]
		result = arr[0]
		
        for i in range(1, n):
            if arr[i] < 0:
                minprod, maxprod = maxprod, minprod
            minprod = min(arr[i], minprod * arr[i])
            maxprod = max(arr[i], maxprod * arr[i])
            
            result = max(result, maxprod)
        return result
```
