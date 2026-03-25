### Best time to buy and sell stock

Leetcode 121 - https://leetcode.com/problems/best-time-to-buy-and-sell-stock/?envType=problem-list-v2&envId=wq9nks7h


## Solution

user input
```python
n = int(input("Enter number of days: "))
prices = list(map(int, input("Enter prices: ").split()))

min_price = float('inf')
max_profit = 0

for price in prices:
    if price < min_price:
        min_price = price
    else:
        profit = price - min_price
        max_profit = max(max_profit, profit)

print(max_profit)
```

```python
from typing import List

class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_price = float('inf')
        max_profit = 0

        for price in prices:
            min_price = min(min_price, price)
            max_profit = max(max_profit, price - min_price)

        return max_profit
```

Time: O(n)
Space: O(1)
