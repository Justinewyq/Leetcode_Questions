# Triplet Sum in Array

https://practice.geeksforgeeks.org/problems/triplet-sum-in-array-1587115621/1

```python
class Solution:
     
    #Function to find if there exists a triplet in the 
    #array A[] which sums up to X.
    def find3Numbers(self,A, n, X):
        # Your Code Here
        s = {}
        for i in range(n - 1):
            for j in range(i + 1, n):
                num = A[i] + A[j]
                if num not in s:
                    s[num] = [i, j]
        #print(s)
        for i in range(n):
            target = X - A[i]
            if target in s and i not in s[target]:
                #print(target, A[i])
                return True
        return False
```
* Time: O(n ^ 2)
* Space: O(n ^ 2)
