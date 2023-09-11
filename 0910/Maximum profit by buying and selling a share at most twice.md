# Maximum profit by buying and selling a share at most twice

https://www.geeksforgeeks.org/maximum-profit-by-buying-and-selling-a-share-at-most-twice/

## Solution

Dynamic Programming

For `prices[i]`, there're 4 status:
1. First time holding a stock. (Could be bought in day i or before.)
2. First time selling a stock. (Could be sold in day i or before.)
3. Second time holding a stock.
4. Second time selling a stock.



```python
import sys

def Solution(price):
  fir_buy = -sys.maxsize
  fir_profit = 0
  sec_buy = -sys.maxsize
  sec_profit = 0
  for i in range(len(price)):
    fir_buy = max(fir_buy, -price[i])
    fir_profit = max(fir_profit, price[i] + fir_buy)
    sec_buy = max(sec_buy, fir_profit - price[i])
    sec_profit = max(sec_profit, price[i] + sec_buy)
  #print(fir_profit, sec_profit)
  print("Max profit is " + str(sec_profit))

price = [2, 30, 15, 10, 8, 25, 80]
Solution(price)
```
