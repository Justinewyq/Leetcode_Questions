# Minimum Swaps for Bracket Balancing

https://practice.geeksforgeeks.org/problems/minimum-swaps-for-bracket-balancing2704/1

## Solution
1. Save the occurence positions of all "[".
2. Iterate the string:
  * Use `cnt` to save the additional `"["` we have.
  * If `"]"` found, `cnt - 1`.
  * If `cnt < 0`, we find an unbalanced `']'`. Find the next `'['` using `left_pos`, and swap them.

```python
class Solution:
    def minimumNumberOfSwaps(self,S):
        # code here 
        left_pos = []
        S = list(S)
        for i in range(len(S)):
            if S[i] == '[':
                left_pos.append(i)
        
        cnt = 0
        ptr = 0
        swaps = 0
        for i in range(len(S)):
            if S[i] == '[':
                cnt += 1
                ptr += 1
            else:
                cnt -= 1
            
            if cnt < 0 and S[i] == ']':
                # find the position of the next '['
                swaps += left_pos[ptr] - i
                S[i], S[left_pos[ptr]] = S[left_pos[ptr]], S[i]
                
                ptr += 1
                cnt = 1
        return swaps
```
