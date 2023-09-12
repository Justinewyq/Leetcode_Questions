# Check if given strings are rotations of each other or not

https://www.geeksforgeeks.org/a-program-to-check-if-strings-are-rotations-of-each-other/

Given a string s1 and a string s2, write a function to check whether s2 is a rotation of s1. 

Examples: 
```
Input: S1 = ABCD, S2 = CDAB
Output: Strings are rotations of each other

Input: S1 = ABCD, S2 = ACBD
Output: Strings are not rotations of each other
```

## Solution
1. Make `s1 = s1 + s1`. `s1 = "ABCDABCD"`.
2. Check if `s2` is a substring of new `s1`.

```python
def Solution(s1, s2):
  s1 = s1 + s1
  if s2 in s1: # O(N)
    return True
  else:
    return False

s1 = "ABCD"
s2 = "ACBD"
print(Solution(s1, s2))
````

* Time: O(N)
