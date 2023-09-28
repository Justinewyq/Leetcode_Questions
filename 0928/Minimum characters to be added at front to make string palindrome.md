# Minimum characters to be added at front to make string palindrome

https://www.geeksforgeeks.org/minimum-characters-added-front-make-string-palindrome/

```
Input: "ABC"
New String: "ABC$CBA"
```
* Calculate the lps list of the new string.
* The last value in the lps list is the length of the longest common prefix & suffix of the new string.
* The rest chars `(len(s) - lps[-1])` is the no. character we should add at front.

```python
def findNext(s, lps_list):
  left = 0
  for i in range(1, len(s)):
    while left > 0 and s[i] != s[left]:
      left = lps_list[left - 1]
    
    if s[i] == s[left]:
      left += 1
    lps_list[i] = left


def Solution(s):
  new = s + "$" + s[::-1]
  lps_list = [0] * len(new)
  findNext(new, lps_list)
  print(lps_list)
  return len(s) - lps_list[-1]

s = "ABC"
#s = "AACECAAAA"
print(Solution(s))
```
