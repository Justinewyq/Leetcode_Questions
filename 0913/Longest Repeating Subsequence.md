# Longest Repeating Subsequence

https://practice.geeksforgeeks.org/problems/longest-repeating-subsequence2004/1

## Solution
Dynamic Programming.
* dp list `dp[i][j]`: the longest subsequece ending with `str[i]` and `str[j]`.
* Equation:
  * If `str[i] == str[j] and i != j`: `dp[i][j] = dp[i - 1][j - 1] + 1`.
  * Else: `dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])`.

```python
class Solution:
	def LongestRepeatingSubsequence(self, str):
		# Code here
        dp = [[0 for i in range(len(str))] for j in range(len(str))]
        
        for i in range(len(str)):
            if str[0] == str[i] and i != 0:
                dp[0][i] = 1
            else:
                dp[0][i] = dp[0][i - 1]
        for i in range(1, len(str)):
            for j in range(1, len(str)):
                if i != j and str[i] == str[j]:
                    dp[i][j] = dp[i - 1][j - 1] + 1
                else:
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
        #print(dp)
        
        return dp[-1][-1]
```

* Time: O(n ^ 2)
* Space: O(n ^ 2)
