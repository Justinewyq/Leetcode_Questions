# Leetcode_Questions
## 08/16
1. 134 - Gas Station
```python
  class Solution:
    def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
        k = 0
        while k < len(gas):
            rest = 0
            dis = 0
            start = k
            i = k
            while rest + gas[i] >= cost[i]:
                if dis == len(gas):
                    return start
                rest = rest + gas[i] - cost[i]
                k += 1
                i = k % len(gas)
                dis += 1
            k += 1
        return -1
        # dis -- how much station we passed
        # rest -- the rest oil left
```
* Time: O(n)

2. 13 - Roman to Integer
```python
class Solution:
    def romanToInt(self, s: str) -> int:
        sym = "IVXLCDM"
        val = [1, 5, 10, 50, 100, 500, 1000]
        result = 0
        i = 0
        while i < len(s):
            if i == len(s) - 1: # the last letter
                result += val[sym.find(s[len(s) - 1])]
                break
            a = sym.find(s[i])
            b = sym.find(s[i + 1])
            if a < b:
                result += val[b] - val[a]
                i += 2
            else:
                result += val[a]
                i += 1
       
        return result
```

3. 58 - Length of Last Word
```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        length = 0
        for i in range(len(s) - 1, -1, -1):
            if length == 0 and s[i] == ' ':
                continue
            elif s[i] == ' ':
                return length
            length += 1
        return length
```

4. 122 - Best Time to Buy and Sell Stock II
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        for i in range(1, len(prices)):
            if prices[i] > prices[i - 1]:
                profit += prices[i] - prices[i - 1]
        return profit
```

5. 6 - Zigzag Conversion
```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if len(s) <= numRows or numRows == 1:
            return s
        result = ""
        for i in range(numRows):
            result += s[i]
            down = 1
            k = i
            while True:
                #print(k)
                #result += s[k]
                if down == 1 and i < numRows - 1: # if not the last row
                    k += 2 * (numRows - i - 1)
                elif down == 0 and i > 0: # if not the first row
                    k += 2 * i
                else:
                    down = abs(1 - down)
                    continue
                if 0 < k < len(s):
                    result += s[k]
                else:
                    break
                down = abs(1 - down)
        return result
```

