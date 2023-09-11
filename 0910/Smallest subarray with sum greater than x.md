# Smallest subarray with sum greater than x

https://practice.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1

* Sliding Window
  
```python
class Solution:
    def smallestSubWithSum(self, a, n, x):
        # Your code goes here
        l = 0
        r = 0
        cur_sum = a[0]
        result = n + 1
        while r < n:
            if cur_sum > x:
                result = min(result, r - l + 1)
                #print(l, r, result, cur_sum)
                cur_sum -= a[l]
                l += 1
            elif r < n - 1:
                r += 1
                cur_sum += a[r]
            else:
                break
        if result == n + 1:
            return 0
        else:
            return result
```

* Time: O(n)
