```python
# Two Pointer Approach
def solution(array):
  left = 0
  right = len(array) - 1
  while left < right:
    if array[left] < 0:
      left += 1
    elif array[right] > 0:
      right -= 1
    else:
      array[left], array[right] = array[right], array[left]
      left += 1
      right -= 1

array = [-12, 11, -13, -5, 6, -7, 5, -3, -6]
solution(array)
print(array)
```

* Time: O(n)
* Space: O(1)
