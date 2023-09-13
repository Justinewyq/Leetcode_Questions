# Longest Palindrome in a String

https://practice.geeksforgeeks.org/problems/longest-palindrome-in-a-string3411/1

## Solution

* For every letter in string, treat it as the center of a potential palindrome.
* Check both odd / even length.


```python
class Solution:
    def longestPalin(self, S):
        # code here
        center = 0
        result = ""
        max_len = 0
        while center < len(S):
            # check odd length string if it is palindromes
            left = center - 1
            right = center + 1
            while left >= 0 and right < len(S) and S[left] == S[right]:
                left -= 1
                right += 1
            cur_len = (right - left) - 1
            if cur_len > max_len:
                max_len = cur_len
                result = S[left + 1 : right]
            
            # check even length string if it is palindrome
            # centered as [center, center + 1]
            left = center
            right = center + 1
            while left >= 0 and right < len(S) and S[left] == S[right]:
                left -= 1
                right += 1
            cur_len = (right - left) - 1
            if cur_len > max_len:
                max_len = cur_len
                result = S[left + 1 : right]
            
            center += 1
        return result
```

* Time: O(n ^ 2)
* Space: O(1)
