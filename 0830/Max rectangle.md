https://practice.geeksforgeeks.org/problems/max-rectangle/1

(Need Optimization. Now Time Limit Exceed.)

Treat each row as a histogram

```python
class Solution:
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
        
    def maxArea(self,M, n, m):
        # code here
        #dp = [[0 for i in range(m)] for j in range(n)]
        result = self.getMaxArea(M[0])
        for i in range(1, n):
            for j in range(m):
                if M[i][j] == 1:
                    M[i][j] = M[i - 1][j] + 1
            result = max(result, self.getMaxArea(M[i]))
        
        return result
```
