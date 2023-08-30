# Kth smallest element

https://practice.geeksforgeeks.org/problems/kth-smallest-element5635/1

## Solution 1
```python
class Solution:
    def kthSmallest(self,arr, l, r, k):
        '''
        arr : given array
        l : starting index of the array i.e 0
        r : ending index of the array i.e size-1
        k : find kth smallest element and return using this function
        '''
        arr.sort()
        return arr[k - 1]
```

## Solution 2
Use quick select.
* `partition(self, arr, l, r)`: Find the position for the pivot.
* If pivot is larger than K-th, search the left part.
* If pivot is smaller than K-th, search the right part.

```python
class Solution:
    def partition(self, arr, l, r):
        cur = l
        for i in range(l, r):
            if arr[i] < arr[r]:
                arr[cur], arr[i] = arr[i], arr[cur]
                cur += 1
        arr[cur], arr[r] = arr[r], arr[cur]
        return cur
    
    def kthSmallest(self,arr, l, r, k):
        '''
        arr : given array
        l : starting index of the array i.e 0
        r : ending index of the array i.e size-1
        k : find kth smallest element and return using this function
        '''
        while True:
            pivot = self.partition(arr, l, r)
            #print(pivot, arr)
            if pivot == k - 1:
                return arr[pivot]
            elif pivot < k - 1: # the element we want to find is in the right part
                #print(pivot + 1, r, k - pivot - 1)
                return self.kthSmallest(arr, pivot + 1, r, k)
            else: # the element is in the left part
                #print(l, pivot - 1, k)
                return self.kthSmallest(arr, l, pivot - 1, k)
```
