# Move all negative numbers to beginning and positive to end with constant extra space

https://www.geeksforgeeks.org/move-negative-numbers-beginning-positive-end-constant-extra-space/

```python
def Solution(arr):
  left = 0
  right = len(arr) - 1
  while left < right:
    if arr[left] < 0:
      left += 1
      continue
    if arr[right] > 0:
      right -= 1
      continue
    arr[left], arr[right] = arr[right], arr[left]

arr = [-12, 11, -13, -5, 6, -7, 5, -3, -6]
Solution(arr)
print(arr)
```

* Space: O(1)
