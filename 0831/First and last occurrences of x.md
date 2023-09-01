# First and last occurrences of x

https://practice.geeksforgeeks.org/problems/first-and-last-occurrences-of-x3116/1

Required Time Complexity: O(logn)

* Use binary search.

```python
def findpos(arr, x):
    if len(arr) == 1:
        if arr[0] == x:
            return 0
        else: 
            return -1
    mid = len(arr) // 2
    #print(arr, mid)
    if arr[mid] == x:
        return mid
    elif arr[mid] > x:
        return findpos(arr[ : mid], x)
    else:
        if mid < len(arr) - 1:
            temp = findpos(arr[mid + 1: ], x)
        else:
            return -1
        if temp == -1:
            return -1
        else:
            return temp + mid + 1

def find(arr,n,x):
    # code here
    left = findpos(arr, x)
    right = left
    while left > 0 and arr[left - 1] == arr[left]:
        left -= 1
    while right < n - 1 and arr[right + 1] == arr[right]:
        right += 1
    return (left, right)
```
