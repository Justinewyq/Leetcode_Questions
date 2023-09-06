# Kadane's Algorithm

https://practice.geeksforgeeks.org/problems/kadanes-algorithm-1587115620/1

```python
class Solution:
    ##Complete this function
    #Function to find the sum of contiguous subarray with maximum sum.
    def maxSubArraySum(self,arr,N):
        ##Your code here
        result = -99999999
        cur_sum = 0
        for i in range(N):
            cur_sum += arr[i]
            result = max(result, cur_sum)
            if cur_sum < 0:
                cur_sum = 0
        return result
```

* Time: O(n)
* Space: O(1)
