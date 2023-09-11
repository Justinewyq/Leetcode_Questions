# Array Subset of another array

https://practice.geeksforgeeks.org/problems/array-subset-of-another-array2317/1

```python
def isSubset( a1, a2, n, m):
    if m > n:
        return "No"
    dic = {}
    for a in a1:
        if a in dic:
            dic[a] += 1
        else:
            dic[a] = 1
    for a in a2:
        if a in dic and dic[a] > 0:
            dic[a] -= 1
        else:
            return "No"
    return "Yes"
```

* Time: O(n + m)
* Space: O(n)
