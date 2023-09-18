# Word Break

https://practice.geeksforgeeks.org/problems/word-break1352/1

## Solution
Dynamic programming

* Dp list: `dp[i]` if `line[ : i]` can be made up from the dictionary.
* In each loop, check if `line[j : i]` is valid, for `j` in `0 ~ i - 1`.

```python
def wordBreak(line, dictionary):
    # Complete this function
    dp = [0 for i in range(len(line) + 1)]
    dp[0] = 1
    
    for i in range(1, len(line) + 1):
        for j in range(i - 1, -1, -1):
            if dp[j] == 1 and line[j : i] in dictionary:
                dp[i] = 1
                break
    return dp[-1] == 1
```
