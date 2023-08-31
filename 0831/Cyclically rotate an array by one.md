# Cyclically rotate an array by one

https://practice.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1

2-points questions.

```python
def rotate( arr, n):
    end = arr[n - 1]
    
    left = n - 2
    right = n - 1

    while left >= 0:
        arr[right] = arr[left]
        right -= 1
        left -= 1
    arr[0] = end
```
