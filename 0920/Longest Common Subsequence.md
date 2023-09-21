# Longest Common Subsequence

## 
1. dp list: `dp[i][j]` -- the LCS of `A[:i]` and `B[:j]`.
2. Equation:
   * `dp[i][j] = dp[i - 1][j - 1] + 1` if `A[i] == B[j]`.
   * `dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])`. 
3. Initialization: 0 for `dp[0][j]` and `dp[i][0]`.

```python
class Solution:
    
    #Function to find the length of longest common subsequence in two strings.
    def lcs(self,x,y,s1,s2):
        
        # code here
        dp = [[0 for j in range(y + 1)] for i in range(x + 1)]
        
        for i in range(1, x + 1):
            for j in range(1, y + 1):
                if s1[i - 1] == s2[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1] + 1
                else:
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
        return dp[-1][-1]
```
