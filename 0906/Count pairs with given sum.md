# Count pairs with given sum

https://practice.geeksforgeeks.org/problems/count-pairs-with-given-sum5022/1

Given an array of N integers, and an integer K, find the number of pairs of elements in the array whose sum is equal to K.

* Time: O(n)
* Space: O(n)

## Solution
* Use `collections.Counter` to save the elements and number of appearences.
* Traverse through the list and find the target value.
* To avoid counting twice, reduce the number of appearences of `arr[i]` once we traverse it.

```python
from collections import Counter

class Solution:
    def getPairsCount(self, arr, n, k):
        # code here
        cnt = Counter(arr)
        result = 0
        for i in range(n):
            target = k - arr[i]
            if target in cnt and cnt[target] > 0:
                result += cnt[target]
                if target == arr[i]:
                    result -= 1
                cnt[arr[i]] -= 1
        return result
```
