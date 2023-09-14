# Edit Distance

https://practice.geeksforgeeks.org/problems/edit-distance3702/1

## Solution
Dynamic programming.

* Dp list: `dp[i][j]` -- the min operation to convert `s[:i]` to `t[:j]`.
* Equation:
  * If `s[i] == t[j]`, `dp[i][j] = dp[i - 1][j - 1]`.
  * Else, we have 3 choices:
    1. Insert: Compare `s[:i]` and `s[:j-1]`.
    2. Delete: Compare `s[:i-1]` and `s[:j]`.
    3. Replace: Compare `s[:i-1]` and `s[:j-1]`.
    * Find the min among these 3.


```python
class Solution:
	def editDistance(self, s, t):
		# Code here
        dp = [[0 for i in range(len(t) + 1)] for j in range(len(s) + 1) ]
        
        for i in range(len(s) + 1):
            for j in range(len(t) + 1):
                if i == 0:
                    dp[i][j] = j
                elif j == 0:
                    dp[i][j] = i
                elif s[i - 1] == t[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1]
                else:
                    dp[i][j] = min(dp[i][j - 1], dp[i - 1][j], dp[i - 1][j - 1]) + 1
        return dp[len(s)][len(t)]
```
