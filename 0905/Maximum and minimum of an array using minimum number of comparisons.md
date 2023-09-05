# Maximum and minimum of an array using minimum number of comparisons

https://www.geeksforgeeks.org/maximum-and-minimum-in-an-array/

```python
def Solution(arr):
  minv = arr[0]
  maxv = arr[0]
  for i in range(len(arr)):
    minv = min(minv, arr[i])
    maxv = max(maxv, arr[i])
  return (minv, maxv)
arr = [22, 14, 8, 17, 35, 3]
print(Solution(arr))
```

* Time: O(n)
* Space: O(1)
