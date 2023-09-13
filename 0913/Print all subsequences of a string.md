# Print all subsequences of a string

https://www.geeksforgeeks.org/print-subsequences-string/

Backtracking problem.

```python
def backtracking(str, mem, start, result):
  if start == len(str):
    return
  for i in range(start, len(str)):
    result.append(mem + str[i])
    backtracking(str, mem + str[i], i + 1, result)

def Solution(str):
  result = []
  backtracking(str, "", 0, result)
  return result

s = "abc"
print(Solution(s))
```
