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

4. 28 - Find the Index of the First Occurrence in a String
```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        return haystack.find(needle)
```


