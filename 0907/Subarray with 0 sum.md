# Subarray with 0 sum

https://practice.geeksforgeeks.org/problems/subarray-with-0-sum-1587115621/1

Given an array of positive and negative numbers. Find if there is a subarray (of size at-least one) with 0 sum.

## Solution
1. Compute the current sum from 0 to i.
2. If the sum appears in the `Set()`, thant means a 0-sum subarray has been found.
3. Else, add the sum to the set.

* Time: O(n)
* Space: O(n)

```python
class Solution:
    
    #Function to check whether there is a subarray present with 0-sum or not.
    def subArrayExists(self,arr,n):
        ##Your code here
        #Return true or false
        s = set()
        cur_sum = 0
        s.add(0)
        for i in range(n):
            cur_sum += arr[i]
            if cur_sum in s:
                return True
            else:
                s.add(cur_sum)
        return False
```
