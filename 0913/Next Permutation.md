# Next Permutation

https://practice.geeksforgeeks.org/problems/next-permutation5226/1

```python
class Solution:
    def nextPermutation(self, N, arr):
        # code here
        pos = N - 2
        while pos >= 0 and arr[pos] >= arr[pos + 1]:
            pos -= 1
        
        if pos == -1:
            left = 0
            right = N - 1
        else:
            next_larger = pos + 1
            while next_larger < N - 1 and arr[next_larger + 1] > arr[pos]:
                next_larger += 1
            #print(arr[next_larger], arr[pos])
            arr[next_larger], arr[pos] = arr[pos], arr[next_larger]
            left = pos + 1
            right = N - 1
        while left < right:
            arr[left], arr[right] = arr[right], arr[left]
            left += 1
            right -= 1
        return arr
```

* Time: O(n)
* Space: O(1)
