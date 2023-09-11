# Palindromic Array

https://practice.geeksforgeeks.org/problems/palindromic-array-1587115620/1

```python
def PalinArray(arr ,n):
    # Code here
    for num in arr:
        s = str(num)
        l = 0
        r = len(s) - 1
        while l < r:
            if s[l] == s[r]:
                l += 1
                r -= 1
                continue
            else:
                return 0
    return 1
```
