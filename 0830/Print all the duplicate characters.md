# Print all the duplicate characters in a string

https://www.geeksforgeeks.org/print-all-the-duplicates-in-the-input-string/

```python
def solution(s):
  dic = {}
  for i in range(len(s)):
    if s[i] in dic:
      dic[s[i]] += 1
    else:
      dic[s[i]] = 1
  for key in dic:
    if dic[key] > 1:
      print(str(key) + ", count = " + str(dic[key]))

s = "geeksforgeeks"
solution(s)
```
