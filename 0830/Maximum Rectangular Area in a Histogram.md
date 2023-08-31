Find the largest rectangular area possible in a given histogram where the largest rectangle can be made of a number of contiguous bars.

* Maintain 2 lists `left_smaller` and `right_smaller`, to save the first smaller elements on the left / right of i-th element.
* So to make `histogram[i]` be the smallest element among a subarray to compute the area of rectangle.

To compute `left_smaller` or `right_smaller`:
* Maintain a stack.
* Iterate through the list:
  * While the current element is smaller than the top of the stack, keep pop.
  * Save the position of first smaller element.
  * Push current element into stack.

```python
class Solution:
    
    #Function to find largest rectangular area possible in a given histogram.
    def getMaxArea(self,histogram):
        #code here
        left_smaller = [-1] * len(histogram)
        right_smaller = [len(histogram)] * len(histogram)
        
        s = [-1]
        for i in range(len(histogram)):
            while len(s) > 1 and histogram[s[-1]] >= histogram[i]:
                s.pop()
            left_smaller[i] = s[-1]
            s.append(i)
        
        s = [len(histogram)]
        for i in range(len(histogram) - 1, -1, -1):
            while len(s) > 1 and histogram[s[-1]] >= histogram[i]:
                s.pop()
            right_smaller[i] = s[-1]
            s.append(i)
        
        #print(left_smaller)
        #print(right_smaller)
        result = 0
        for i in range(len(histogram)):
            cur = histogram[i] * (right_smaller[i] - left_smaller[i] - 1)
            result = max(result, cur)
        return result
```
