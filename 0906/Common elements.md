# Common elements

https://practice.geeksforgeeks.org/problems/common-elements1132/1

Given three arrays sorted in increasing order. Find the elements that are common in all three arrays.

```
Example 1:

Input:
n1 = 6; A = {1, 5, 10, 20, 40, 80}
n2 = 5; B = {6, 7, 20, 80, 100}
n3 = 8; C = {3, 4, 15, 20, 30, 70, 80, 120}
Output: 20 80

Explanation: 20 and 80 are the only common elements in A, B and C.
```
## Solution

* Using 3 pointers for the 3 arrays.
* If the 3 values are not equal, right shift the index of smallest value.

```python
class Solution:
    def commonElements (self,A, B, C, n1, n2, n3):
        # your code here
        ptr1, ptr2, ptr3 = 0, 0, 0
        result = []
        while ptr1 < n1 and ptr2 < n2 and ptr3 < n3:
            #print(A[ptr1], B[ptr2], C[ptr3])
            if A[ptr1] == B[ptr2] and A[ptr1] == C[ptr3] and A[ptr1] not in result:
                result.append(A[ptr1])
                ptr1 += 1
                ptr2 += 1
                ptr3 += 1
                
            elif A[ptr1] <= B[ptr2] and A[ptr1] <= C[ptr3]:
                ptr1 += 1
            elif B[ptr2] <= A[ptr1] and B[ptr2] <= C[ptr3]:
                ptr2 += 1
            #elif C[ptr3] <= A[ptr1] and C[ptr3] <= B[ptr2]:
            else:
                ptr3 += 1
                
        return result
```

* Time: O(n1 + n2 + n3)
* Space: O(1)
