# Rearrange array in alternating positive & negative items with O(1) extra space

https://www.geeksforgeeks.org/rearrange-array-alternating-positive-negative-items-o1-extra-space/

## Solution
* Iterate through the array and make sure the current value has correct sign.
* If an element is not in the correct place, find the first value with an opposite sign behind, and rotate the array in between.

```python
def rotate(arr, i, j):
  temp = arr[j]
  while j > i:
    arr[j] = arr[j - 1]
    j -= 1
  arr[i] = temp

def Solution(arr):
  # When we find a value in wrong position
  # find is used to find the following value with opposite sign
  find = 0
  cur = -1 # the supposed sign of the current value
  for i in range(len(arr)):
    
    if cur * arr[i] > 0:
      cur *= -1
      continue
    else:
      find = cur
      j = i + 1
      #print(cur, i, arr[i], arr)
      while j < len(arr) and find * arr[j] <= 0:
        j += 1
      if j < len(arr) and find * arr[j] > 0:
        rotate(arr, i, j)
      cur *= -1

arr = [1, 2, 3, -4, -1, 4]
#arr = [-5, -2, 5, 2, 4, 7, 1, 8, 0, -8]
Solution(arr)
print(arr)
```

* Time: O(n^2)
* Space: O(1)
