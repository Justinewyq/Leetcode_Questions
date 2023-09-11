# Given Array of size n and a number k, find all elements that appear more than n/k times

https://www.geeksforgeeks.org/given-an-array-of-of-size-n-finds-all-the-elements-that-appear-more-than-nk-times/

* Use dictionary.
  
```python
def Solution(arr, k):
  dic = {}
  for i in arr:
    if i in dic:
      dic[i] += 1
    else:
      dic[i] = 1

  times = len(arr) // k
  result = []
  for k in dic.keys():
    if dic[k] > times:
      result.append(k)
  return result

arr = [3, 1, 2, 2, 1, 2, 3, 3]
k = 4
print(Solution(arr, k))
```

* Time: O(n)
* Space: O(n)
