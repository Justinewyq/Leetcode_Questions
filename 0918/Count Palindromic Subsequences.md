# Count Palindromic Subsequences

https://practice.geeksforgeeks.org/problems/count-palindromic-subsequences/1

### 1. Brute Force Solution
```python
class Solution:
    # Your task is to complete this function
    # Function should return an integer
    def checkPalindrome(self, string):
        left = 0
        right = len(string) - 1
        while left < right:
            if string[left] == string[right]:
                left += 1
                right -= 1
            else:
                return False
        return True
        
    def backtracking(self, string, mem, start):
        if start == len(string):
            return 0
        result = 0
        for i in range(start, len(string)):
            if self.checkPalindrome(mem + string[i]):
                result += 1
            result += self.backtracking(string, mem + string[i], i + 1)
        return result
        
    def countPS(self,string):
        # Code here
        result = self.backtracking(string, "", 0)
        return result % int(1e9 + 7)
                
```

### 2. Dynamic Programming

* Dp list: `dp[i][j]` -- the number of palindrome of substring `string[i : j]`
* Initialization: `dp[-1][-1] = 1`
* Equation:
  * If `string[i] == string[j]`: `dp[i][j] = dp[i + 1][j] + dp[i][j - 1] + 1`.
  * Else: `dp[i][j] = dp[i + 1][j] + dp[i][j - 1] - dp[i + 1][j - 1]`.

```python
class Solution:
    # Your task is to complete this function
    # Function should return an integer
    def countPS(self,string):
        # Code here
        dp = [[0 for i in range(len(string))] for j in range(len(string))]
        
        for i in range(len(string) - 1, -1, -1):
            for j in range(i, len(string)):
                if j == i:
                    dp[i][j] = 1
                else:
                    if string[i] == string[j]:
                        dp[i][j] = dp[i + 1][j] + dp[i][j - 1] + 1
                    else:
                        dp[i][j] = dp[i + 1][j] + dp[i][j - 1] - dp[i + 1][j - 1]
        #print(dp)
        return dp[0][-1] % int(1e9 + 7)
```
* Time: O(n ^ 2)
* Space: O(n ^ 2)
