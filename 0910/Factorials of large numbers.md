# Factorials of large numbers

https://practice.geeksforgeeks.org/problems/factorials-of-large-numbers2508/1

## Solution
Since the result is too large, we use a list to store thr factorial result.

Use traditional multiplication method.

```python
class Solution:
    def mult(self, n, x):
        # reverse the list of int, so to append carry at the end in O(1)
        x = x[::-1]
        carry = 0
        for i in range(0, len(x)):
            mul = n * x[i] + carry
            x[i] = mul % 10
            carry = mul // 10
        while carry:
            x.append(carry % 10)
            carry = carry // 10
        return x[::-1]
        
    def factorial(self, N):
        #code here
        result = [1]
        for i in range(2, N + 1):
            result = self.mult(i, result)
        return result
        # Recurse
        #if N == 1:
        #    return [1]
        #else:
        #    return self.mult(N, self.factorial(N - 1))
```
