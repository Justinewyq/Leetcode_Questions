# Write a program to reverse an array or string

https://www.geeksforgeeks.org/write-a-program-to-reverse-an-array-or-string/

```python
def Solution(arr):
  left = 0
  right = len(arr) - 1
  while left < right:
    arr[left], arr[right] = arr[right], arr[left]
    left += 1
    right -= 1

arr = [4, 5, 1, 2]
print("Before: ", arr)
Solution(arr)
print("After: ", arr)
```
