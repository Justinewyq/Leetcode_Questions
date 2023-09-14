# Permutations of a given string

https://practice.geeksforgeeks.org/problems/permutations-of-a-given-string2041/1

* Backtracking problem.
* To avoid repetation, on the same level of tree, one should perform pruning.

  
```python
class Solution:
    def backtracking(self, S, used, mem, result):
        if len(mem) == len(S):
            result.append(mem)
            return
        i = 0
        while i < len(S):
            #print(mem, i, used)
            if used[i] == 0:
                #print(mem, used)
                used[i] = 1
                self.backtracking(S, used, mem + S[i], result)
                used[i] = 0
                i += 1
                # pruning
                while i < len(S) and S[i] == S[i - 1]:
                    i += 1
            else:
                i += 1
    
    def find_permutation(self, S):
        # Code here
        S = ''.join(sorted(S))
        used = [0 for i in range(len(S))]
        result = []
        self.backtracking(S, used, "", result)
        return result
```
