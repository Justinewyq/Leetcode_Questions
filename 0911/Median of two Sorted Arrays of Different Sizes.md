# Median of two Sorted Arrays of Different Sizes

https://www.geeksforgeeks.org/median-of-two-sorted-arrays-of-different-sizes/

* Find the median while merging.

```python
def Solution(a, b):
  length = len(a) + len(b)
  total = 0
  # pointers to traverse arrays a and b
  x, y = 0, 0
  firv = 0
  while x < len(a) or y < len(b):
    if x < len(a) and y < len(b):
      if a[x] <= b[y]:
        curnum = a[x]
        x += 1
      else:
        curnum = b[y]
        y += 1
    elif x < len(a):
      curnum = a[x]
      x += 1
    else:
      curnum = b[y]
      y += 1
    if total == length // 2:
      if length % 2 == 0:
        return (firv + curnum) // 2
      else:
        return curnum
    total += 1
    firv = curnum

#a = [-5, 3, 6, 12, 15]
#b = [-12, -10, -6, -3, 4, 10]
a = [2, 3, 5, 8]
b = [10, 12, 14, 16, 18, 20]
print(Solution(a, b))
```

* Time: O(N + M)
* Space: O(1)
