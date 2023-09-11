# Three way partitioning

https://practice.geeksforgeeks.org/problems/three-way-partitioning/1

Apply Partition twice.
```python
class Solution:
    #Function to partition the array around the range such 
    #that array is divided into three parts.
    def partition(self, arr, l, r, k):
        ptr = l
        for i in range(l, r + 1):
            if arr[i] < k:
                arr[ptr], arr[i] = arr[i], arr[ptr]
                ptr += 1
        #print(ptr, r)
        #arr[ptr], arr[r] = arr[r], arr[ptr]
        return ptr
            
	def threeWayPartition(self, array, a, b):
	    # code here 
        bound = self.partition(array, 0, len(array) - 1, a)
        #print(bound)
        self.partition(array, bound, len(array) - 1, b)
```

* Time: O(n)
* Space: O(1)
