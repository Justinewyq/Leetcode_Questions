# Count the Reversals

https://practice.geeksforgeeks.org/problems/count-the-reversals0401/1

```python
def countRev (s):
    # your code here
    if len(s) % 2 == 1:
        return -1
    
    stack = []
    result = 0
    
    for p in s:
        if p == '{':
            stack.append(p)
        else:
            if len(stack) == 0:
                stack.append('{')
                result += 1
            else:
                stack.pop()
    result += len(stack) // 2
    return result
```
