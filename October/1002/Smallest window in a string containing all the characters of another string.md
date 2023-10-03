# Smallest window in a string containing all the characters of another string

https://practice.geeksforgeeks.org/problems/smallest-window-in-a-string-containing-all-the-characters-of-another-string-1587115621/1

* Keep a counter for chars in string `p`.
* When the window contains all chars in `p`, try to decrease the size of window. (By moving the begining of window to right.)
* Else, increase the size of window.
  * If a letter is contained in `p`, decrease the counter.

```python
class Solution:
    
    #Function to find the smallest window in the string s consisting
    #of all the characters of string p.
    def smallestWindow(self, s, p):
        #code here
        counter = {}
        for c in p:
            if c in counter:
                counter[c] += 1
            else:
                counter[c] = 1
        pairs = 0
        
        begin = 0
        end = 0
        result = len(s) + 1
        left = 0
        while end < len(s) or pairs == len(p):
            if end < len(s) and s[end] in counter:
                counter[s[end]] -= 1
                if counter[s[end]] >= 0:
                    pairs += 1
                # while substring of s contains p
                # move the left side of window
                while pairs == len(p):
                    if end - begin + 1 < result:
                        result = end - begin + 1
                        left = begin
                    if s[begin] in counter:
                        counter[s[begin]] += 1
                        if counter[s[begin]] > 0:
                            pairs -= 1
                    begin += 1
            end += 1
        if result <= len(s):
            return s[left : left + result]
        else:
            return -1
```

* Time: O(n)
* Space: O(m)
