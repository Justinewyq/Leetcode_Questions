# Longest consecutive subsequence

https://practice.geeksforgeeks.org/problems/longest-consecutive-subsequence2449/1

```python
class Solution:
    
    # arr[] : the input array
    # N : size of the array arr[]
    
    #Function to return length of longest subsequence of consecutive integers.
    def findLongestConseqSubseq(self,arr, N):
        #code here
        arr.sort()
        cur = 1
        result = 0
        for i in range(1, N):
            if arr[i] == arr[i - 1] + 1:
                cur += 1
            elif arr[i] == arr[i - 1]:
                continue
            else:
                result = max(result, cur)
                cur = 1
        result = max(result, cur)
        return result
```
